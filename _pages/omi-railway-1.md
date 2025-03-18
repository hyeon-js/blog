---
layout: post
title: "오미 철도 운행 정보 구현 1) 시간표 만들기"
featured-img: omi-railway-1.png
---

오미 철도의 시간표 기반 운행정보 기능을 만들기로 했어요.

홈페이지에 시간표가 올라와있긴 하지만, 사람이 읽기에만 편해요. 텍스트로 되어있는 `.pdf 파일`이긴 한데, 드래그로 글자를 선택하면 지맘대로 선택되어요.

![image]({{site.url}}{{site.baseurl}}/assets/images/omi-railway/0.png)

<br/>

별도의 페이지에서 역별 시간표를 확인할 수 있는데,

![image]({{site.url}}{{site.baseurl}}/assets/images/omi-railway/1.png)

<br/>

여긴 HTML로 되어있어요. 차라리 `.pdf 파일`을 보고 하나하나 엑셀에 옮겨 적는 것보다, 저 홈페이지를 자동으로 긁어서 `.csv 파일`로 저장하는 것이 더 편할 것 같아요.

![image]({{site.url}}{{site.baseurl}}/assets/images/omi-railway/2.png)

<br/>

그런고로 `node.js`를 사용해서 내용을 알아서 긁어와서

![image]({{site.url}}{{site.baseurl}}/assets/images/omi-railway/3.png)

<br/>

`.csv 파일`로 저장하는 소스코드를 작성해서 실행했어요.

![image]({{site.url}}{{site.baseurl}}/assets/images/omi-railway/4.png)

<br/>

그런데 생각보다 열차 운행 계획이 복잡했어요. 노선이 3개 있는데, 열차가 다른 노선으로 들어갈 수도 있고 그러지 않을 수도 있고, 중간부터 시작할 수도 있고 중간까지만 운행할 수도 있고

아무튼 `.pdf 파일`로 배포된 시간표를 참고하면서 하나하나 직접 보정했어요.

![image]({{site.url}}{{site.baseurl}}/assets/images/thumb/omi-railway-1.png)

<br/>

다른 노선들의 시간표도 다 긁어온 뒤에, `본선만 운행하는 열차`와 타 `노선도 운행하는 열차`로 나눠서 저장했어요.

![image]({{site.url}}{{site.baseurl}}/assets/images/omi-railway/5.png)

<br/>

어차피 사용할 때에는 `JSON`으로 바꿀 예정이라 복잡해도 딱히 상관은 없어질 예정이에요.
