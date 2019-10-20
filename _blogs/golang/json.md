---
title: Golang에서 JSON Unmarshal시 주의할 점
subTitle: 
category: 
tags: 
createdat: 2019-10-18 13:17:00
updatedat: 2019-10-18 13:17:00
---

```go
func ExampleUnmarshal() {
	data := []byte("{\"test\": \"test\", \"TEST\": \"TEST\"}")
	var d struct {
		LowerCase string `json:"test"`
	}
	err := json.Unmarshal(data, &d)
	if err != nil {
		log.Println(err)
	}

	fmt.Println(d.LowerCase)

	// Output:
	// test
}
```

위의 테스트 코드를 실행하면 결과가 어떻게 될까?

```bash
--- FAIL: ExampleUnmarshal (0.00s)
got:
TEST
want:
test
```

테스트는 실패한다. `Unmarshal`할 때 JSON의 `test` 속성값이 나올 것이라고 생각했는데 아니었다. 그렇다면 `struct`에 두 속성 모두 추가해주면 어떻게 될까?

```golang
func ExampleUnmarshal() {
	data := []byte("{\"test\": \"test\", \"TEST\": \"TEST\"}")
	var d struct {
		LowerCase string `json:"test"`
		UpperCase string `json:"TEST"`
	}
	err := json.Unmarshal(data, &d)
	if err != nil {
		log.Println(err)
	}

	fmt.Println(d.LowerCase)
	fmt.Println(d.UpperCase)

	// Output:
	// test
	// TEST
}
```

위의 테스트는 통과한다. 왜그럴까? golang 문서를 찾아보면 다음과 같은 글을 찾아볼 수 있다.

To unmarshal JSON into a struct, Unmarshal matches incoming object keys to the keys used by Marshal (either the struct field name or its tag), preferring an exact match but also accepting a case-insensitive match.

JSON 속성의 대소문자를 구분하지 않는다! 만약 처리하려는 JSON의 속성값이 대소문자로 구분되어있는 값이 있다면 주의깊게 처리해야 한다.

## Sources

* <https://golang.org/pkg/encoding/json/#Unmarshal>

