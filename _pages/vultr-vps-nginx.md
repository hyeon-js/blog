---
layout: post
title: "Vultr에서 VPS 구매 및 nginx 설치하기"
featured-img: vultr-vps-nginx.jpg
---

# Vultr 회원가입

구글에 `Vultr`를 검색하면 크레딧으로 250 달러를 줄 것 같긴 한데,

![image]({{site.url}}{{site.baseurl}}/assets/images/vultr-vps-nginx/0.png)

<br />
전 지인이 준 초대 링크로 가입했어요. 초대 링크로 들어가면 메인 화면으로 리다이렉트될텐데, 원래 그게 정상이라고 하니 그냥 가입

![image]({{site.url}}{{site.baseurl}}/assets/images/vultr-vps-nginx/1.png)

<br />
아입할 때 입력했던 이메일도 활성화시키고

![image]({{site.url}}{{site.baseurl}}/assets/images/vultr-vps-nginx/2.png)

<br />
카드도 등록했어요.

![image]({{site.url}}{{site.baseurl}}/assets/images/vultr-vps-nginx/3.png)

<br />
`I just want to link my credit card -$0.00 deposit`를 체크해야 불필요한 과금이 발생하지 않아요.

![image]({{site.url}}{{site.baseurl}}/assets/images/vultr-vps-nginx/4.png)

***
<br />

# VPS 생성 (구매)

`Product` 탭에 들어가면 나오는 화면에서 오른쪽 위에 있는 `+` 버튼을 누르면 나오는 메뉴에서 `Deploy New Server`를 누르면 서버를 추가할 수 있어요.

![image]({{site.url}}{{site.baseurl}}/assets/images/vultr-vps-nginx/5.png)

<br />
이것저것 뭐가 많이 있는데, 전 `Cloud Compute`에 있는 `AMD High Performance` 중 한 달에`$6`짜리 플랜을 골랐어요. 리전은 `한국`, 운영체제는 `우분투`로 했구요.

![image]({{site.url}}{{site.baseurl}}/assets/images/vultr-vps-nginx/6.png)

<br />
백업이라거나 그런건 전부 필요하지 않는 관계로 다 안쓰는걸로 하고

![image]({{site.url}}{{site.baseurl}}/assets/images/vultr-vps-nginx/7.png)

<br />
`Deploy Now` 버튼을 눌러서 생성!

![image]({{site.url}}{{site.baseurl}}/assets/images/vultr-vps-nginx/8.png)

<br />
히히 서버당

![image]({{site.url}}{{site.baseurl}}/assets/images/vultr-vps-nginx/9.png)

***
<br />

# 서버에 ssh로 접속해서 nginx 설치하기

아래에 있는 명령어를 통해 서버에 원격으로 접속했어요. `fingerprint` 어쩌고 뜨면서 뭐라고 하면 일단 `yes` 입력하고 엔터치면 접속이 될거에요.
```
$ ssh root@{서버아이피주소}
//이후에 비밀번호 입력
```
![image]({{site.url}}{{site.baseurl}}/assets/images/vultr-vps-nginx/10.png)

<br />
서버 아이피나 비밀번호 같은건 서버 페이지?에서 볼 수 있어요.

![image]({{site.url}}{{site.baseurl}}/assets/images/vultr-vps-nginx/11.png)

<br />
아래 명령어를 통해 nginx를 설치했어요. 중간에 뭐 재싫행할꺼냐고 물어보는 그런건 능력것 `OK` 누르면 될거에요.
```
$ sudo apt-get update
$ sudo apt-get install nginx
```
![image]({{site.url}}{{site.baseurl}}/assets/images/vultr-vps-nginx/12.png)

***
<br />

# 방화벽 열기

`80번 포트`를 열어줘야 해요. 다음 명령어를 통해 열 수 있어요.
```
$ ufw allow 80
```

![image]({{site.url}}{{site.baseurl}}/assets/images/vultr-vps-nginx/13.png)

<br />
이제 웹 브라우저에 서버 ip를 입력해보면, 이런식으로 홈페이지 접속이 될거에요.

![image]({{site.url}}{{site.baseurl}}/assets/images/thumb/vultr-vps-nginx.jpg)
