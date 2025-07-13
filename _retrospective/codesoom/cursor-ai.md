---
title: 코드숨 커서AI 트렌드&활용백과 참여 회고
subTitle:
category:
tags:
createdat: 2025-06-05 20:15:00
updatedat: 2025-07-13 23:23:11
---

코드숨에서 커서AI 트렌드&활용백과 책을 가지고 스터디를 4주 동안 진행했다.  

따라 하기만 하면 금방 읽을 수 있는 책이라서 책 자체 내용을 다루기보다는 실무
예제를 공유하거나 관련 팁을 공유를 하려고 했다. 그래서 실무에서 커서를 쓰면서 잘
됐던 사례들을 기록해놨다가 공유했다. 대부분 잘된 경우는 프롬프트에 내가 알고
있는 컨텍스트를 자세히 기록했을 때 잘 동작했다. 그리고 실제로 실행하기 전에
계획을 먼저 작성하게 하고 계획을 검토하고 수정한 다음에 커서가 코드를 작성했을
때도 잘 동작했다.  

스터디 3번째 시간에는 실제로 실무에서 할 일을 가져와서 문제를 같이 해결하는
라이브 코딩을 했다. 좋은 프롬프트 예제를 많이 보더라도 직접 작성하는 것은 완전
다르다. 그래서 다들 어려워했지만, 프롬프트를 작성해서 그 시간에 문제를 쉽게 해결할 수 있었다.
그때 썼던 프롬프트는 다음과 같다.

```markdown
목표: 경험 상점 상세 페이지에 경험상점 후기 중에서 선별된 후기 목록을 노출한다.
노출 조건
- 대상 상품 : 판매 중인 상품의 후기만 노출해야 한다. (종료, 오픈예정 제외)
- 이미지 1장 이상있고, 후기 텍스트가 5자 이상이어야 한다.
- 평점 4.0 이상이어야 한다.
노출 순서 
- 최근 등록된 순 (최근에 등록된 리뷰가 맨 앞에)
노출 개수
- 최대 6개
노출 데이터
- 작성자 이름, 등록일, 평점, 후기 내용, 해당 후기의 경험상점 메인사진과 타이틀.
구현해야 되는 기능
- 후기를 누르면, 해당 경험상점 상세 페이지의 후기 탭으로 이동
- 하단에 경험상점 타이틀을 클릭하면, 해당 경험상점 페이지로 이동
```

이 프롬프트로 거의 완벽하게 구현했고 실제로 이때 작성한 코드로 아직도 동작하고
있다.  

AI와 협업을 잘하기 위해서는

1. 내가 구현할 것을 명확하게 기술해야 한다. 잘 쓰여진 기능정의서 혹은 기획서를
   작성한다고 생각하면 된다.

예시:

```markdown
AnchorTabs는 상품 상세 카테고리로 바로 스크롤 할 수 있는 버튼이 있는 탭입니다. 
해당 영역으로 스크롤 했을 경우 해당 영역의 버튼이 활성화되고, 버튼을 누르면 해당 영역으로 스크롤하고 
버튼이 활성화 됩니다.

문제: 카테고리가 많을 경우 가로로 스크롤 되는데, 다른 버튼들이 안보입니다.

할일:
- 스크롤 해서 카테고리가 활성화 될 때 활성화된 버튼이 화면의 가운데로 오도록 자연스럽게 스크롤 해야 합니다.
- 카테고리 버튼을 눌러서 스크롤할 때도 버튼이 화면의 가운데로 오도록 자연스럽게 스크롤 해야 합니다.
```

2. 내가 알고 있는 숨겨진 컨텍스트를 충분히 전달해야 한다. 코드에서 드러나지 않는
   사실들을 충분히 설명해 주어야 한다.
3. 알고 있다면, 구현을 참고하거나 필요한 파일들을 컨텍스트에 직접 지정하는 것이
   좋다. 예를들어서 비슷한 기능을 구현한 파일이 있다면 해당 파일을 컨텍스트에
   직접 지정해야 한다. 혹은 구현했을 때 영향이 있을 파일들이 있다면 직접 지정해주는 것이 좋다.
4. 만약 내가 생각하는 구현 순서나 계획이 있다면 자세히 말해줘야 한다. 예를들어서
   특정 기능 구현을 위해서 ERD를 먼저 변경하고 나서 서비스를 구현하고, 그 서비스
   변경에 따른 프론트 변경 코드를 구현해달라고 지시할 수 있다.
5. 쓸데없는 파일은 정리해야 한다. 쓸데없는 파일들을 AI가 참고하여 잘못된 결과가 나올 수 있다.
6. AI가 한 번에 모든 과정을 진행하지 말고 중간 중간에 멈춰달라고 해야한다. 한
   번에 너무 많은 변경사항은 이해하기 어려워서 잘못된 코드를 고칠 수 없다.

예시:

```markdown
경험상점의 카테고리를 불러와서 보여주는 기능을 만들어 주세요. 단 한 번에 실행하지말고 계획을 하나씩 실행하고, 실행이 끝나면 멈춰서 다음 지시가 있을때 까지 기다려 주세요.
```

7. 프로젝트 룰에 컨벤션을 기록하여 전달해야 한다. AI가 매번 코드를 작성하기 전에
   컨벤션을 파악하고 작성할 수는 없기 때문에, 참고해야할 컨벤션들은 프로젝트
   룰에 미리 작성해 놓는다.

예시:

```md
## Package manager

패키지 매니저는 `pnpm`을 사용합니다.

예시

```bash
$ pnpm install lodash
```

## Data fetching

원격 데이터를 불러올 때는 server action을 사용합니다.

### 예시

```tsx
// action.ts
import { z } from 'zod'

const exampleDto = z.object({
  title: z.string()
})

export const exampleAction = authActionClient
  .metadata({ actionName: 'exampleAction' })
  .schema(exampleDto)
  .action(async ({ ctx, parsedInput: { title } }) => {
    const { userId } = ctx

    const { id } = await exampleService.createExample(title)
    return id
  })

// example-component.tsx
export function ExampleComponent() {
  const createExample = useAction(exampleAction)

  const handleClick = async () => {
    const result = await createExample.executeAsync()
    if (result?.serverError) {
      console.log('serverError is occurred: ', result.serverError)
      return
    }

    console.log('createdId', result.data)
  }

  return (
    <button onClick={handleClick} type="button">
      예제 생성하기
    </button>
  )
}
```

## Date Library

날짜 라이브러리는 `Day.js`를 사용합니다.

### 예시

```ts
import { dayjs } from '@core/utils'

const now = dayjs.tz()
const formatted = now.format('YYYY-MM-DD')
```

## 참고

- [커서AI 트렌드&활용백과 \| 주홍철 저자(글) \| 스마트북스](https://product.kyobobook.co.kr/detail/S000216110195)
