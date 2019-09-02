---
title: 로드 밸런싱이란?
subTitle: 
category: 
tags: 
createdat: 2019-09-02 10:27:00
updatedat: 2019-09-02 10:27:00
---

컴퓨터들, 컴퓨터 클러스터, 네트워크 링크, 중앙 처리 장치 또는 디스크 드라이브와
같이 여러 컴퓨팅 리소스에 대한 워크로드 분배를 향상시키는 것을 말한다. 
로드밸런싱은 하나의 리소스에 과부하를 피하고 자원사용을 최적화 하는 것을 목표로
한다. 단일 컴포넌트를 사용하는 대신 여러 컴포넌트를 사용하는 것은 중복성을 통해
신뢰성과 가용성을 증가시킨다. 로드 밸런싱은 일반적으로 멀티 레이어 스위치 또는 
도메인 이름 시스템 서버 프로세스와 같은 전용 소프트웨어 또는 하드웨어가 
포함된다.  

로드 밸런서는 일반적으로 Layer 4 와 Layer 7 두 개를 많이 말한다. Layer 4 로드 
밸런서는 네트워크 및 전송 계층 프로토콜 (IP, TCP, FTP, UDP)에서 발견 된 
데이터에 작용합니다. 

Layer 7 로드 밸런서는 HTTP와 같은 애플리케이션 계층 프로토콜에서 데이터를
기반으로 요청을 분배합니다. HTTP 헤더, 쿠키 또는 애플리케이션 메시지 자체 내의 
데이터 (예 : 특정 매개 변수 값)와 같은 애플리케이션 별 데이터를 기반으로 요청을 
분배 할 수 있습니다.

요청은 두 가지 유형의 로드 밸런서 모두에서 수신하며 구성된 알고리즘을 기반으로 
특정 서버에 분배됩니다. 일부 산업 표준 알고리즘은 다음과 같습니다.

* Round robin
* Weighted round robin
* Least connections
* Least response time

로드 밸런서는 응용 프로그램의 "상태"를 모니터링하고 적시에 응답 할 수 있는 서버
및 응용 프로그램에만 요청을 보내서 안정성과 가용성을 보장합니다.

## Sources 

* <https://devcentral.f5.com/s/articles/what-is-load-balancing-24740>
* <https://en.wikipedia.org/wiki/Load_balancing_(computing)>
* <https://en.wikipedia.org/wiki/Multilayer_switch#Layer_4_Load_Balancer>
* <https://www.f5.com/services/resources/glossary/load-balancer>
