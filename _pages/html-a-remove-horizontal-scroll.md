---
layout: post
title: "&lt;a&gt; 태그 사용시 종종 지멋대로 생성되는 가로 스크롤 없애기"
featured-img: html-a-remove-horizontal-scroll.png
---

HTML `<a>` 태그를 사용했을 때, 그 안에 들어간 문구가 너무 길고 띄어쓰기도 없다면 지멋대로 가로 스크롤이 생기곤 해요.
따로 설정해둔 가로 길이 제한 등을 무시하고 지멋대로 만들어버려요.

그럴 때는 CSS를 사용해서 줄바꿈 기준을 글자 단위로 만들어버리면 해결되는거에요.

```css
word-break: break-all;
```