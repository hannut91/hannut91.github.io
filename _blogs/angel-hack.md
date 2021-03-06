---
title: 엔젤핵 해커톤 참여 회고
subTitle:
category:
tags:
createdat: 2020-07-21 00:37:00
updatedat: 2020-07-21 00:37:00
---

## 같이

어떻게 하면 처음 다짐했던 학습의 의지를 잃지 않고 유지할 수 있을까? 많이 고민했다. 서로 응원하는 투두리스트도 만들어보고 작심삼일 목표를 짧게 잡는 투두리스트도 만들어보고, 공부를 했을 때 느낀 감정을 기록하는 투두리스트도 만들려고 했었다. 하지만 이태원 코딩 도장에서 같이 공부를 하면서 깨달은 것은, 같이 하는 것만큼 의지를 불태울 수 있는 건 없다는 것이다. 혼자서는 절대 못할 것들도 같이 했을 때는 그 분위기에 휩쓸려 어쩔 수 없이 하게 된다. 하지만 코로나 때문에 모여서 같이 공부하는 환경이 제약이 있거나 우리처럼 이태원 코딩 도장이 없는 사람들은 어떻게 해야 하는가? 그 사람들도 `같이` 할 순 없을까?  

이태원 코딩 도장에서 포모도로 타이머를 이용해서 집중해서 공부하고 적절히 휴식을 취하여 몸 관리도 하며 스터디를 했다. 그래서 이 경험을 다른 사람들도 느꼈으면 해서 원격으로 포모도로 타이머를 공유하는 앱을 만들었다. 만들고 싶다 생각만 하고 실제로 만들기에는 두려움 때문에 시도조차 못했는데, 해커톤이라는 핑계삼아 만들었다.  

서로 접속해서 매칭을 하면 랜덤하게 서로 매칭이 되고 하나의 타이머를 공유한다. 이 타이머 시간 동안을 집중해서 공부를 해야 한다. 만약 딴짓을 하거나 집중하지 못해 앱을 종료하면 페널티를 받게 된다. 무사히 공부를 완료하면 점수를 얻는다. 그래서 등급이 생기고 낮은 등급의 사람들은 낮은 사람들끼리 매칭이 되고 높은 동급인 사람들은 높은 등급인 사람들만 매칭이 되어 공부를 열심히 하는 사람들은 더 열심히 할 수 있는 환경을 만들고 싶었다. 하지만 제한된 시간 때문에 매칭하는 것만 만들었다.  

매칭이 이루어지면 타이머가 시작되고 서로 카메라로 화면을 공유하여 딴짓을 하지 않는지 서로 감시할 수 있다. 자세한 내용은 데모 영상에서 확인할 수 있다.

## 테스트 숙련도의 문제

정공법으로 돌파하고 싶었다. 그래서 테스트 커버리지를 100%를 맞추고, CI/CD를 구현하고 작업을 했다. 하지만 같이 참여한 팀원들의 테스트에 대한 숙련도가 낮아서 진행이 쉽지 않았다. 짝 프로그래밍을 해도 익숙해지는 데 시간이 걸렸다. 테스트를 작성해야 버그가 발견했을 때 드는 비용을 일정하게 유지할 수 있다고 생각하여 이게 더 빠른 길이라고 생각했는데 판단 미스였다. 결국 클라이언트는 컴포넌트 테스트를 포기했다. 서버는 테스트를 작성하여 복잡한 소켓 통신도 안전하게 작업할 수 있었다.  

다음번에는 팀원들의 숙련도를 충분히 높인 후에 진행해야겠다.

## 깨진 창문

커버리지를 100%를 유지했는데 마지막 날에 깨졌다. 체력 고갈과 시간의 압박 때문에 결국 커버리지 한계를 90%로 낮췄고, 낮추는 순간 커버리지는 보지도 않게 됐다. 깨진 창문 이론을 다시 한 번 몸으로 느꼈다.

## 중요한 것에 집중하자

처음에 어떻게 시작할지 어려워서, 로그인이 필수적인 앱을 아니었지만 로그인을 구현하기로 했다. 근데 로그인이 3일이나 걸렸다. 다음번에는 과감하게 정말 필요한 것에만 집중해서 개발을 해야겠다.

## Sources

* 깃헙 - <https://github.com/poongdeong/poongdeong>
* 데모영상 - 유튜브 - <https://www.youtube.com/watch?v=C82uXRYDR8E&feature=youtu.be>
