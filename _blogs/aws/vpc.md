---
title: Amazon VPC란 무엇인가
subTitle:
category: 
tags: 
createdat: 2019-10-31 19:12:00
updatedat: 2019-10-31 19:12:00
---

## VPC

* Amazon Virtual Private Cloud(VPC)는 사용자의 AWS 계정 전용 가상 네트워크. 
* AWS Cloud에 있는 가상 네트워크들과 논리적으로 격리되어 있다.

## Subnet

* VPC의 IP주소 범위
* AWS 리소스들을 특정한 서브넷에 실행할 수 있다.
* 퍼블릭 인터넷에 연결할며면 퍼블릭 서브넷을 사용해야 한다.
* 프라이빗 서브넷은 인터넷에 연결되지 않는다.

## Route table

* 네트워크 트래픽이 어디로 전송될지 결정하는데 사용되는 규칙 집합.

## Internet gateway

* 인터넷 게이트웨이는 인스턴스들을 인터넷에 연결할 수 있도록 한다.

## Endpoint

* 인터넷 게이트웨이, NAT 디바이스, VPN 연결 또는 AWS Direct Connect 연결없이 PrivateLink를 통해 지원되는 AWS 서비스 및 VPC 엔드 포인트 서비스에 VPC를 비공개로 연결할 수 있음.

## Default VPC

* 아마존 계정을 만들면 가용영역마다 `default VPC`가 있다.
* EC2 인스턴스를 만들 때 따로 지정하지 않으면 `default VPC`로 지정이 된다.
* internet gateway가 기본으로 포함되어 있고, 기본 서브넷은 퍼블릭 서브넷이다.
* 각 인스턴스는 프라이빗 IPv4주소와 퍼블릭 IPv4주소를 가지고 있다.
* 이 인스턴스들은 인터넷 게이트웨이를 통해 인터넷과 통신이 가능한다.

## Nondefault VPC

* 기본으로 `default VPC`가 있지만 만들수도 있다.
* VPC안에 있는 인스턴스들이 외부에 리소스들과 어떻게 접근할 것인지 결정할 수 있다.
* Nondefault 서브넷에 만든 인스턴스들은 프라이빗 IPv4주소만 있다.

### Accessing the Internet

* VPC내에서 서로 통신은 가능하지만 인터넷에 접근할 수는 없다.
* 인터넷 게이트웨이를 통해 인터넷에 접속가능하게 할 수 있다.
* 또는 VPC의 인스턴스가 인터넷에 대한 아웃 바운드 연결을 시작하지만 인터넷에서 원치 않는 인바운드 연결을 방지하기 위해 IPv4 트래픽에 NAT (Network Address Translation) 장치를 사용할 수 있습니다.
* NAT는 여러 개인 IPv4 주소를 단일 공용 IPv4 주소로 매핑한다.
* NAT 장치는 Elastic IP 주소를 가지며 인터넷 게이트웨이를 통해 인터넷에 연결된다. 
* NAT 장치를 통해 프라이빗 서브넷의 인스턴스를 인터넷에 연결하면 인스턴스에서 인터넷 게이트웨이로 트래픽을 라우팅하고 모든 응답을 인스턴스로 라우팅 할 수 있다.
* Amazon 제공하는 IPv6 CIDR 블록을 VPC와 연결하고 인스턴스에 IPv6 주소를 할당 할 수 있다. 
* 인스턴스는 인터넷 게이트웨이를 통해 IPv6을 통해 인터넷에 연결할 수 있다. 
* 또는 인스턴스가 송신 전용 인터넷 게이트웨이를 사용하여 IPv6을 통해 인터넷에 대한 아웃 바운드 연결을 시작할 수 있다. 
* IPv6 트래픽은 IPv4 트래픽과 별개라서 라우팅 테이블에는 IPv6 트래픽에 대한 별도의 라우팅이 포함되어야한다.

## Sources

* <https://docs.aws.amazon.com/en_pv/vpc/latest/userguide/what-is-amazon-vpc.html>