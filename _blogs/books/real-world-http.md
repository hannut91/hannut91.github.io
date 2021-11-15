---
title: 리얼월드 HTTP 서평
subTitle:
category:
tags:
createdat: 2021-06-26 15:44:00
updatedat: 2021-06-26 15:44:00
---

HTTP/3가 나왔는데 HTTP/1.0, 1.1 그리고 2를 배워야 할까?  

배워야 한다. 왜냐하면 HTTP 프로토콜은 확장성이 있는 프로토콜이며 브라우저 측이 사용자의 편의성 향상을 목표로 어떻게 발전해 왔는지를 살펴볼 가치가 있다. 그 과정에서 HTTP의 4가지 기본 요소들은 변하지 않았고, 왜 HTTP가 지금의 모습이 됐는지를 이해하면 앞으로의 HTTP를 이해하는 데 도움이 될 것이다.

## HTTP의 4가지 기본 요소

* 메서드와 경로
* 헤더
* 바디
* 스테이터스 코드

### HTTP 0.9

최초 버전인 HTTP/0.9는 HTML 문서를 요청해서 가져오기만 하는 단순한 프로토콜이었다.  

최초 사양을 HTTP/0.9라고 부르지만, HTTP/1.0 사양이 화제가 되고 나서부터 1.0이전 버전이라는 의미로 0.9라고 불리게 됐다.
 
### HTTP 1.0

브라우저가 문서를 요청하면 서버는 데이터를 반환한다는 웹의 기본 뼈대는 여기서 이미 완성되었다. 하지만 이 프로토콜로는 한계가 있었다.

* 하나의 문서를 전송하는 기능밖에 없다.
* 통신되는 모든 내용은 HTML 문서로 가정했으므로, 다운로드할 콘텐츠의 형식을 서버가 전달할 수단이 없었다.
* 클라이언트 쪽에서 검색 이외의 요청을 보낼 수 없었다.
* 새로운 문장을 전송하거나 갱신 또는 삭제할 수 없었다.
* 요청이 올바른지 서버가 올바르게 응답했는지 알 수 없었다.

그래서 헤더의 추가적인 정보를 이용해서 파일의 형색을 명시하거나, 메서드를 이용해 다양한 요청을 수용하고, 상태 코드를 이용해서 어떤 문제인지 더 명확하게 명시하고 바디에 데이터를 포함해서 전송할 수 있게 되었습니다.

### HTTP 1.1

1. `Keep-Alive`와 `파이프라이닝`을 이용해 통신 고속화가 이루어졌다.
2. `TLS`에 의한 암호화 통신을 지원하게 되었다.
3. `PUT`메서드와 `DELETE`메서드가 표준화가 되었다.
4. `OPTIONS`, `TRACE`, `CONNECT` 메서드가 추가되었다.
5. 프로토콜 업그레이드를 할 수 있게 됐다.
6. 가상 호스트를 지원했다.
7. 전체를 한 번에 전송하지 않고 작게 나눠 전송하는 chunk가 추가됐다.
8. 데이터를 한 번에 보내는 것이 아니라 받아들일 수 있는지 물어보고 나서 데이터를 보내는 2단계 전송을 할 수 있게 됐다.

### HTTP 2

HTTP/2의 목적은 통신 고속화뿐이다.

1. 스트림을 사용해 바이너리 데이터를 다중으로 송수신하는 구조로 변경됐다.
  * 텍스트 기반 프로토콜에서 바이너리 기반 프로토콜로 변화했다.
2. 스트림 내 우선순위 설정과 서버 사이드에서 데이터 통신을 하는 서버 사이드 푸시를 구현했다.
3. 헤더가 압축하게 되었다.

## Sources

* 코드숨 리얼월드 HTTP 스터디 회고 - <https://hannut91.github.io/retrospective/codesoom/real-wrold-http>
* 스터디 정리 - GitHub - <https://github.com/CodeSoom/study-real-world-http>
* RFC7540 - <https://datatracker.ietf.org/doc/html/rfc7540>
* 리얼월드 HTTP - 교보문고 - <http://www.kyobobook.co.kr/product/detailViewKor.laf?barcode=9791162240908>