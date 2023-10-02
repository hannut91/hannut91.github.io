---
title: Ginkgo로 Golang에서 BDD스타일로 테스트 작성하기
subTitle:
category: 
tags: 
createdat: 2019-02-05 23:20:14
updatedat: 2023-10-02 15:43:21
---

## 설치

```
$ go install github.com/onsi/ginkgo/v2/ginkgo
$ go get github.com/onsi/gomega/...
```

## 시작하기

### test suite파일 만들기

Ginkgo테스트를 실행하기 위해서는 test suite파일을 만들어야 합니다.

```
$ cd path/to/books
$ ginkgo bootstrap
```

`bootstrap`을 명령어를 실행하면 books_stuite_test.go파일이 다음과같이 생성됩니다.

```
package books_test

import (
    "testing"

    . "github.com/onsi/ginkgo/v2"
    . "github.com/onsi/gomega"
)

func TestBooks(t *testing.T) {
    RegisterFailHandler(Fail)
    RunSpecs(t, "Books Suite")
}
```

package 이름이 books가 아니라 `books_test`인것을 볼 수 있는데 books패키지의 캡슐화를 할 수 있다.
이는 필수가 아닌 옵션으로 필요가 없다면 `books`로 패키지이름을 변경하면 된다.
`TestBooks`가 go lang에서 `testing` test인데 Go의 테스트 러너가 이 함수를 실행한다.
`RegisterFailHandler(Fail)`은 함수를 Gomega로 보낼 때 사용하는 함수이다.
`RunSpecs`는 Ginkko가 test suite를 실행하도록 명령내리는 것입니다. 

```
$ go test
```

혹은

```
$ ginkgo
```

명령어로 테스트를 실행할 수 있다.

### 테스트 작성하기

다음 명령어를 사용해서 테스트 파일을 생성할 수 있습니다.

```
$ ginkgo generate book
```

이러면 `book_test.go`파일이 생성됩니다.

### Marking specs as failed

테스트가 실패하는 경우 다음과 같이 작성하여 테스트를 실패시킬 수 있다.
```
Fail("Failure reason")
```

Fail이 실행 될 경우 현재 테스트 되고 있는 spec은 멈춘다. panic은 rescue되어 다음 테스트로 넘어가게 된다.
하지만 만약 테스트가 goroutine을 실행하고 있을 경우 Ginkgo가 panic을 rescue할 수 없다.
이럴경우는 다음과같이 goroutine안에 `GinkgoRecover()`를 실행하여야 한다.

```
It("panics in a goroutine", func(done Done) {
    go func() {
        defer GinkgoRecover()

        Ω(doSomething()).Should(BeTrue())

        close(done)
    }()
})
```

오메가가 만약 false를 리턴한다면 Gomega는 Fail함수를 실행할 것이고 panic이 발생할 것입니다. GinkgoRecover가 recover하여 test suite가 멈추는것을
방지할 수 있습니다.

### Logging output
`GinkgoWriter`라는 `io.Writer`전역변수가 있는데 이 Wirter에 Write하면 테스트가 실패할 경우 결과들을 출력해준다. 이는 테스트를 실행할 떄
```
$ ginkgo -v 

or

$ go test -ginko.v
```

라고 실행하여야 결과를 볼 수 있다.

만약 테스트가 실행중에 강제로 테스트가 종료된다면 지금까지 가지고 있는 데이터들을 출력해준다.

## 참고

- [Ginkgo](https://onsi.github.io/ginkgo)
