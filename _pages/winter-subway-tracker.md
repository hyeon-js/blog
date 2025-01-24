---
layout: post
title: "윈터 랩핑 열차 추적기"
featured-img: winter-subway-tracker.png
---

서울 지하철 2호선에서 에스파 윈터 생일 기념 랩핑 열차를 운행한다는 소식을 들었어요.
운행 기간은 `2024년 12월 20일`부터 `2025년 1월 19일`까지.

마침 랩핑 열차가 어디에 있는지 확인할 수 있는 기능을 마침 간단하게 구현할 수 있을 것 같아서, 토이 프로젝트로 진행했어요.

![image]({{site.url}}{{site.baseurl}}/assets/images/winter-subway-tracker/0.jpg)

<br/>
웹사이트로 윈터 랩핑 열차 추적기를 구현한 모습. 잠실새내역에 도착했다고 뜨고,

![image]({{site.url}}{{site.baseurl}}/assets/images/winter-subway-tracker/1.png)

<br/>
실제로도 잠실새내역에 도착한 상태에요. 직접 가서 찍은 사진

![image]({{site.url}}{{site.baseurl}}/assets/images/winter-subway-tracker/2.jpg)

<br/>
열차 내부는 이런식으로 윈터 생일 광고로 덮여있어요. `차량번호가 2485인 칸`만 저렇게 되어있어요.

![image]({{site.url}}{{site.baseurl}}/assets/images/winter-subway-tracker/3.jpg)

<br/>
또다른 내부 사진

![image]({{site.url}}{{site.baseurl}}/assets/images/winter-subway-tracker/4.jpg)

<br/>
민정아 생일축하해

![image]({{site.url}}{{site.baseurl}}/assets/images/winter-subway-tracker/5.jpg)

<br/>
윈터 생일 광고 랩핑은 `차량번호가 2485인 칸`에 있으니, `해당 칸을 포함하고 있는 열차(편성번호가 285인 열차)`가 어디에 있는지 찾으면 돼요.


이미 [열차의 실시간 위치를 불러오는 것](https://hyeon-js.github.io/subway/)은 구현해본 상태에요. 그 열차들의 편성번호도 알아올 수 있지만, 여려가지 이유로 굳이 구현하지는 않은 상태였어요.
그러니, 285 편성 추적기를 만들면 완성.
