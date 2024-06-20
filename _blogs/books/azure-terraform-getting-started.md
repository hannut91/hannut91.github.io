---
title: Terraform으로 Azure VM을 만들려면 어떻게 해야하나요?
subTitle:
category: 
tags: 
createdat: 2024-06-19 17:14:00
updatedat: 2024-06-20 16:26:11
---

## Step 1

프로바이더와 플러그인 버전을 명시합니다.

```terraform
# 사용하는 플러그인의 버전을 명시합니다. 필수는 아니지만 버전마다 다르게 동작하는 불상사를 피하기 위해 지정하는 것을 권장합니다.
# 버전은 https://github.com/hashicorp/terraform-provider-azurerm 여기서 tag로 확인합니다.
terraform {
  required_providers {
    azurerm = {
      source  = "hashicorp/azurerm"
      version = "=3.108.0"
    }
  }
}

# 프로바이더를 정의합니다. 테라폼에서 프로바이더는 특정 클라우드 서비스와 상호작용하게 하는 플러그인입니다.
# features는 필수 입력값입니다. 지금은 아무런 설정없이 기본값으로 설정되어 있습니다.
provider "azurerm" {
  features {}
}
```

## Step 2

리소스 그룹을 정의합니다. 이제부터 만드는 리소스들은 이 그룹에 넣습니다.

```terraform
resource "azurerm_resource_group" "group" {
  name     = "my-resource-group"
  location = "Korea Central"
}
```

## Step 3

네트워크를 정의합니다.

```terraform
resource "azurerm_virtual_network" "network" {
  name                = "my-network"
  address_space       = ["10.0.0.0/16"]
  location            = azurerm_resource_group.group.location
  resource_group_name = azurerm_resource_group.group.name
}

resource "azurerm_subnet" "subnet" {
  name                 = "my-subnet"
  resource_group_name  = azurerm_resource_group.group.name
  virtual_network_name = azurerm_virtual_network.network.name
  address_prefixes     = ["10.0.2.0/24"]
}
```

## Step 4

네트워크 인터페이스를 정의합니다.

```terraform
# 퍼블릭 ip를 받기 위해 정의를 하고 네트워크 인터페이스에서 할당합니다. 이게 없으면 외부에서 접근할 수 없습니다.
resource "azurerm_public_ip" "vm_public_ip" {
  name                = "my-public-ip"
  location            = azurerm_resource_group.group.location
  resource_group_name = azurerm_resource_group.group.name
  allocation_method   = "Dynamic"
}

resource "azurerm_network_interface" "network-interface" {
  name                = "my-network-interface"
  location            = azurerm_resource_group.group.location
  resource_group_name = azurerm_resource_group.group.name

  ip_configuration {
    name                          = "internal"
    subnet_id                     = azurerm_subnet.subnet.id
    private_ip_address_allocation = "Dynamic"
    public_ip_address_id          = azurerm_public_ip.vm_public_ip.id
  }
}
```

## Step 5

시큐리티 그룹을 만듭니다. 여기선 ssh연결을 위한 22포트와 http 80포트만
열었습니다. 사용 사례에 따라 다른 포트 번호를 지정할 수 있습니다.

```terraform
resource "azurerm_network_security_group" "nsg" {
  name                = "my-nsg"
  location            = azurerm_resource_group.group.location
  resource_group_name = azurerm_resource_group.group.name
}

resource "azurerm_network_security_rule" "allow_80" {
  name                        = "allow_80"
  priority                    = 100
  direction                   = "Inbound"
  access                      = "Allow"
  protocol                    = "Tcp"
  source_port_range           = "*"
  destination_port_range      = "80"
  source_address_prefix       = "*"
  destination_address_prefix  = "*"
  resource_group_name         = azurerm_resource_group.group.name
  network_security_group_name = azurerm_network_security_group.nsg.name
}

resource "azurerm_network_security_rule" "allow_22" {
  name                        = "allow_22"
  priority                    = 110
  direction                   = "Inbound"
  access                      = "Allow"
  protocol                    = "Tcp"
  source_port_range           = "*"
  destination_port_range      = "22"
  source_address_prefix       = "*"
  destination_address_prefix  = "*"
  resource_group_name         = azurerm_resource_group.group.name
  network_security_group_name = azurerm_network_security_group.nsg.name
}

resource "azurerm_network_interface_security_group_association" "nsg_association" {
  network_interface_id      = azurerm_network_interface.network-interface.id
  network_security_group_id = azurerm_network_security_group.nsg.id
}
```

## Step 6

VM을 만듭니다.

```terraform
resource "azurerm_linux_virtual_machine" "vm" {
  name                  = "my-vm"
  location              = azurerm_resource_group.group.location
  resource_group_name   = azurerm_resource_group.group.name
  network_interface_ids = [azurerm_network_interface.network-interface.id]
  size                  = "Standard_B1ls"
  admin_username        = "azureuser"

  admin_ssh_key {
    username   = "azureuser"
    # 로컬 컴퓨터에서 만든 key를 사용하고 싶을 경우 이렇게 지정해줄 수 있습니다.
    public_key = file("~/.ssh/azure-key.pub")
  }

  os_disk {
    caching              = "ReadWrite"
    storage_account_type = "Premium_LRS"
  }

  # 어떤 이미지로 만들지 지정합니다. 여기서는 Ubuntu 24.04 Minimal을 사용하고 있습니다.
  source_image_reference {
    publisher = "Canonical"
    offer     = "0001-com-ubuntu-minimal-noble-daily"
    sku       = "minimal-24_04-daily-lts-gen2"
    version   = "24.04.202403090"
  }
}
```

## Step 7

이제 작성한 코드로 리소스를 만듭니다.

```bash
terraform init # 처음에만 실행합니다.
terraform apply
```

## VM에 사용할 이미지 찾는 방법

```bash
# Ubuntu 24.04버전을 찾을 때 예시
az vm image list --location koreacentral --output table --publisher Canonical --all --sku 24_04
```

그러면 Architecture, Offer, Publisher, Sku, Urn, Version이 테이블로 출력됩니다. 이걸 테라폼에서 사용하려면 다음과 같이 작성할 수 있습니다.

```terraform
source_image_reference {
  publisher = "Canonical"
  offer     = "0001-com-ubuntu-server-jammy"
  sku       = "22_04-lts"
  version   = "latest"
}
```

## 참고

- [Find Azure Marketplace image information using the Azure CLI](https://learn.microsoft.com/en-us/azure/virtual-machines/linux/cli-ps-findimage)
