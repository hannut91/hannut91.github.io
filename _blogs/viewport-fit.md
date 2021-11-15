---
title: viewport-fit이란?
subTitle:
category:
tags:
createdat: 2021-11-15 20:22:00
updatedat: 2021-11-15 20:22:00
---

## Viewport란?

브라우저의 viewport란 웹 콘텐츠를 볼 수 있는 window의 영역을 말합니다. 볼 수 있는 화면보다 큰 
내용은 스크롤을 해서 보여줄 수 있습니다.

### 모바일 페이지에서의 문제

모바일 페이지처럼 좁은 화면에서는 일반적으로 넓은 가상의 window나 viewport에서 페이지를 렌더링한 후 
결과를 축소하여 보여줍니다. 예를들어 모바일 화면의 길이가 640px이고 컨텐츠의 가로가 980px이라면 
640px에 맞게 축소되어 렌더링 됩니다. 그러면 사용자는 불편하게 줌 인 하거나 줌 아웃하여 콘텐츠를 
봐야합니다. 모바일에 최적화 되지 않았기 때문입니다.

## viewport 메타 태그

위와 같은 문제를 해결하기 위하여 viewport 매타 태그가 등장했습니다. 이 태그를 이용하면 viewport의
사이즈와 스케일을 조정할 수 있고, 작은 사이즈의 브라우저에 최적화된 콘텐츠를 보여줄 수 있습니다.

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

위에서 `width`는 viewport의 사이즈를 지정하는 것인데, 픽셀 같은 단위로 입력할 수도 있지만 
`device-width`같은 스크린의 가로 픽셀값을 지정할 수 있습니다.

## viewport-fit이란?

viewport-fit이란 단순한 사각형모양의 디스플레이가 아닌 디스플레이를 위한 속성이다.  

## viewport-fit을 왜 사용하는가?

viewport 메타 태그 덕분에 네모난 화면의 작은 모바일 디바이스에 최적화된 콘텐츠들을 보여줄 수 
있었습니다. 그런데 iPhone X가 등장하면서 단순히 네모난 모양이 아닌 다양한 모양의 디스플레이가 나오기 
시작했습니다.  

네모난 모양의 컨텐츠들을 보여주고 추가적으로 꽉찬 모양의 컨텐츠를 보여주고 싶을 때 viewport-fit속성을 
사용할 수 있습니다.

## viewport-fit을 어떻게 사용할 수 있는가?

![normal](https://user-images.githubusercontent.com/14071105/141789085-dbf06225-0200-4196-917f-e6dd63d42910.png)

기본적으로 iPhone X도 모바일에 맞게 잘 컨텐츠를 보여주고 있습니다. 하지만 옆에 있는 영역까지 모두 채워서 
보여주고 싶을 때 `viewport-fit`속성을 `cover`로 설정하면 다음과 같이 보여줄 수 있습니다.

![normal2](https://user-images.githubusercontent.com/14071105/141789403-13c77e36-4429-4ecf-b7f7-51ff0b3e90e8.png)

이제 전체 화면에 꽉차게 보여주고 있는 것을 확인할 수 있습니다. 하지만 글자가 잘려버려 사용자가 정보를 올바르게 읽을 수 없게 되었습니다.
이럴 때는 `safe-area-inset-*`속성을 이용하면 다음과 같이 보여줄 수 있다.

![normal3](https://user-images.githubusercontent.com/14071105/141789887-800c8b04-22ad-493d-b527-a81e587e3634.png)

이제 전체화면을 사용하면서도 사용자가 모든 정보를 올바르게 볼 수 있게 되었습니다.

## Sources

* Designing Websites for iPhone X - <https://webkit.org/blog/7929/designing-websites-for-iphone-x/>
* Viewport concepts - <https://developer.mozilla.org/en-US/docs/Web/CSS/Viewport_concepts>
* Using the viewport meta tag to control layout on mobile browsers - <https://developer.mozilla.org/en-US/docs/Web/HTML/Viewport_meta_tag>
* Configuring the Viewport - <https://developer.apple.com/library/archive/documentation/AppleApplications/Reference/SafariWebContent/UsingtheViewport/UsingtheViewport.html>
