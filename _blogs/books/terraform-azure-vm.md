---
title: Terraform에서 Azure VM리소스를 한 번에 여러개 작성하려면 어떻게 해야 하나요?
subTitle:
category:
tags:
createdat: 2024-06-20 17:32:00
updatedat: 2024-06-20 18:20:07
---

```terraform
resource "azurerm_linux_virtual_machine" "vm" {
  name = "my-server"
  
  # ... 생략
}
```

이런 리소스를 정의했다고 가정해 보겠습니다. 동일한 리소스를 여러 개 만들고
싶다면 다음과 같이 `count`를 사용할 수 있습니다.

```terraform
resource "azurerm_linux_virtual_machine" "vm" {
  name = "my-server"

  count = 5

  # ... 생략
}
```

그러면 동일한 스펙으로 5개가 생깁니다. 하지만 그대로 실행해 보면 다음과 같이
에러가 발생합니다.

```bash
already exists - to be managed via Terraform this resource needs to be imported into the State. # ... 생략
```

`name`이 `my-server`로 고정되어 있어서 동일한 이름으로 4개를 더 만들려고 하니
에러가 발생합니다. 이럴 경우 index를 사용해서 이름을 고유하게 만들 수 있습니다.

```terraform
resource "azurerm_linux_virtual_machine" "vm" {
  name = "my-server-${count.index}"

  count = 5

  # ... 생략
}
```

## 참고

- [The count Meta-Argument](https://developer.hashicorp.com/terraform/language/meta-arguments/count)
