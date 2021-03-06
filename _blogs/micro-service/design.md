---
title: 마이크로 서비스 신규 기능 설계하기
subTitle: 마이크로 서비스 신규 기능 설계하기
category: 
tags: 
createdat: 2019-08-26 11:07:00
updatedat: 2019-08-26 11:07:00
---

마이크로 서비스 인 액션 4장을 읽고 정리해보았습니다.

## 신규 기능 설계하기

마이크로 서비스 애플리케이션에 새로운 기능을 설계하려면 신중하고 합리적인
범위를 설정해야 한다. 새로운 서비스를 개발하거나 기존 서비스를 확장할 시기와
서비스간의 경계, 그리고 어떻게 서비스들이 협업할지를 결정해야 한다.  

잘 설계된 서비스에는 3가지 핵심 특징이 있다.
* 단일 역량을 담당한다.
* 독립적으로 배포 가능하다
* 교체가 가능하다

## 비즈니스 문제 이해

시장조사나 고객 인터뷰, 영향도 매핑 등의 몇가지 기법을 활용해 비즈니스 문제에
대해 조사와 분석을 할 수 있다.

## 비즈니스 역량의 범위 지정하기

어떤 기능을 구축할지, 이미 존재하는 서비스와 새로운 서비스에서 그
기능을 어떻게 지원할지 정해야 한다. 올바른 서비스의 목적을 선택하는 것이
중요하다.  

서비스의 범위를 정하는 것은 3가지 전략이 있다.
* 비즈니스 역량 또는 Bounded context에 따라 지정
* Use case에 따라 지정
* 변동 가능성에 따라 지정

## 역량과 도메인 모델링

비즈니스 역량이란 조직이 가치를 창출하고 비즈니스 목표를 만족하기 위해 조직이
수행하는 것이다. 이는 도메인 주도 설계(DDD)접근 방식과 밀접하게 관련이 있다.
Bounded context란 도메인 내의 모든 솔루션은 여러 Bounded context로 구성될 수
있다. 각 context내의 모델은 응집도가 높고 실 세계와 동일한 뷰를 가진다. 각
context는 다른 context와 강력하고 명확한 경계를 가진다. 이 것은 서비스의 범위를
지정할 때 자연스러운 출발점이 된다. 각 context는 솔루션의 여러 영역 간 경계를
나타낸다. context는 서비스와 비즈니스 역량의 영역에 직접 매핑된다. 각 Bounded
context는 내부 동작을 감추면서 다른 context에 API를 제공한다. 내부/공개의
구분은 서비스가 진화하는 데 유용한 메커니즘을 제공한다. 시스템 초기에는
고수준의 경계를 나타내는 큰 크기의 서비스를 구축하는 것을 선택할 수 있다.
시간이 지나면서 내포된 컨텍스트의 행동을 노출하는 별도의 서비스로 분리할 수
있다. 이렇게 하면 비즈니스 로직의 복잡도가 증가해도 교체하기 쉽고 높은 응집도를
유지할 수 있다.  

하지만 비즈니스 역량기준으로 분리하는 것은 비즈니스와 대상 도메인에 대한 상당한
이해를 요구한다. 충분한 정보가 없거나 잘못된 가정을 올바른 설계 결정을 내렸는지
확신할 수 없다. 모든 비즈니스에서 요구사항을 이해하는 것은 복잡하고 시간이
걸리며 반복적인 과정이다. 비즈니스 역량접근법은 대규모 비즈니스 경계를 포함하는
큰 크기의 서비스 초기 개발에 치우쳐 있다. 감당할 만한 수준의 응집도와 교체성을
유지하기 위해 서비스를 쪼갤 필요가 있다.

## 유스케이스로 범위 정하기

범위를 정하는 다른 방법은 애플리케이션 내의 동사 또는 유스케이스를 식별하고
이런 책임에 해당하는 서비스를 구축하는 것이다. 다음과 같은 경우에 유용한
방법이다.
* 역량이 하나의 도메인에 명확하게 속하지 않거나 여러 도메인과 상호작용하는 경우
* 구현할 유스케이스가 복잡하고 다른 서비스에 두면 단일 책임 원칙을 위반하는
  경우

### 액션과 저장소

여러 고수준의 마이크로 서비스가 큰 규모의 하위 비즈니스 역량에 접근하는 패턴이
있는데 이런 팬턴은 밥 마틴의 클린 아키텍처나 앨리스테어 콕번의 육각형
아키텍처롸 유사하다. 이 아키텍처는 개념적으로 우아하지만 마이크로 서비스
시스템에 현명하게 적용해야 한다. 하위 역량을 상태 저장소로 대하는 것은 빈약하고
우둔한 서비스를 낳을 수 있다. 이런 서비스들은 다른 고수준의 서비스의 중재
없이는 아무런 동작도 할 수 없기 때문에 자율적이지 못하다. 또한 유용한 모든
동작을 수행하는데 필요한 원격 호출과 긴 서비스 연결의 수가 증가한다. 또한 이
방식은 하위 저장소가 단단히 결합할 위험이 있어 서비스를 독립적으로 배포하는
능력을 저해한다. 이런 오류를 피하려면 세분화단 동작 지향 서비스(action-oriented
services)를 개발하기 전에 내부에서 외부로 설계해 큰 크기의 유용한 역량을
마이크로 서비스를 설계하는 것이 좋다.

### 조율과 자율적 구성

유스케이스를 반영하는 서비스를 설계할 때 광범위한 범위의 책임 중에서 어떤
부분을 서비스가 맡을지 고려하는 것이 중요하다. 조율과 자율적 구성 기법을
균형있게 택하면 자율성이 떨어지는 서비스를 구축할 위험을 줄일 수 있다.

## 변동 가능성에 따라 범위 정하기

기능적 분해는 애플리케이션의 현재 필요성에 치우쳐 있고 어떻게 진화할지에
대해서는 명확하게 고려하지 않는다. 순수한 기능적 접근 방법은 새로운 또는
진화하는 요구사항에 대해 유연하지 못한 서비스를 만들어 시스템의 미래 성장에
제약을 줄 수 있다. 그래서 변경의 위험을 중가시킨다. 그러므로 시스템의 기능을
고려할 뿐만 아니라 애플리케이션의 어느 부분이 앞으로 변경될지도 고려해야 한다.

## 기술적 역량

기술 역량은 비즈니스 역량의 크기와 복잡성을 제한해 다른 마이크로 서비스를
지원하고 단순화할 때 사용해야 한다. 이런 역량을 별도의 서비스로 분리할 때
독립적으로 변경될 것 같은 변경가능성을 포착해 서비스 재사용성을 극대화한다.

## 모호함 다루기

문제 도메인에 대한 이해가 불완전하거나 부정확할 수 있다. 모든 비즈니스 문제의
필요성을 이해하는 것은 복잡하고 시간 소모적이고 반복적인 과정이다. 지금
당장보다는 향후 서비스를 어떻게 사용할지 고려해야 한다. 그러나 단기간의
요구사항과 장기간의 서비스 유연성 간의 경쟁에 직면할 수 있다. 마이크로 서비스에
최적화되지 않은 서비스의 분리는 비용이 들 수 있다.

### 큰 규모의 서비스로 시작하기

때때로 서비스 경계가 의심스러울 때는 큰 규모의 서비스를 구축하는 것이 낫다.

### 향후 분해를 위한 준비

일반적으로 좋은 소프트웨어는 명확한 공개 API를 사용해 내부 모듈 경계를 잘
유지한다.

### 제거와 이관

큰 서비스로 시작했다면 시간이 지나면서 기존 서비스에서 새로운 마이크로 서비스를
떼어내거나 제거할 필요성이 발견될 것이다. 가장 중요한 것은 이것을 사용하는 
서비스가 깨지지 않도록 하고 적시에 새로운 교체 서비스로 이관해야 한다는 것이다.
새로운 서비스를 떼어내려면 확장-이관-축소 패턴(expand-migrate-contract
pattern)을 적용해야 한다.

1. 우선 확장해야 한다. 대상 기능을 새로운 서비스로 추출한다.
2. 예전 서비스의 사용자를 새로운 서비스로 이관한다.
3. 원래 서비스에서 불필요한 코드를 제거해 축소한다.

## 조직의 서비스 오너십

바운디드 컨텍스트 자체는 조직에서 여러 팀이 애플리케이션의 소유권을 효과적으로
나눠 갖는 방법이다. 특정 바운디드 컨텍스트의 서비스를 소유하는 팀을 구성하는
것은 콘웨이의 법칙을 반대로 이용하는 것이다.  

서비스의 소유와 전달을 여러 팀에 나눈 것은 3가지 의미가 있다.
1. 제한된 제어: 서비스 의존성에 대한 인터페이스 또는 성능에 대해 완전한
   제어권을 갖지 않을 수 있다.
2. 설계 제약: 서비스 컨슈머의 요구사항은 서비스 계약을 제약할 것이다. 서비스를
   변경할 때 컨슈머를 고려해야 한다. 마찬가지로 다른 기존 서비스가 제공하는
   기능이 설계에 잠재적인 영향을 준다.
3. 다양한 속도로 개발: 여러 팀이 소유한 서비스는 팀의 크기, 우선순위에 따라
   다른 속도로 변경하고 발전할 것이다.

이런 서비스 오너십의 분산은 커다란 어려움을 초래하지만 몇가지 전술이 도움이 될
수 있다.

1. 개방: 모든 엔지니어가 모든 코드를 조회하고 변경할 수 있게 하는 것은
   방어적인 것을 줄이고 다른 팀이 서로의 작업을 이해하도록 돕고 장애물을
   줄여준다.
2. 명확한 인터페이스: 명확하게 잘 문서화된 서비스 인터페이스는 커뮤니케이션의
   부담을 줄여주고 전체적인 품질을 개선한다.
3. DRY에 대해 덜 걱정하기: 마이크로 서비스의 접근 방식은 효율성 보다는 전달에
   무게를 둔다.
4. 명백한 기대: 팀은 운영 서비스의 성능, 특성에 대해 명확한 기대치를 설정해야
   한다.

## Sources

* 마이크로 서비스 인 액션 - 모건 부르스, 파울로 페레이라
