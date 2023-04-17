---
layout: post
title: "VMWare에 macOS High Sierra 설치하기"
featured-img: vmware-macos.png
---

새로 가상머신을 추가하려고 하는데, macOS가 안보일거에요.

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/0.png)

<br />
[여기를 눌러서](https://github.com/paolo-projects/unlocker/releases) unlocker를 다운로드 받으시고, 압축을 푸신 뒤에 `win-install.bat` 파일을 관리자 권한으로 실행해주세요.

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/1.png)

<br />
실행이 끝나면

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/2.png)

<br />
이렇게 `Apple Mac OS X`가 보일거에요.

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/3.png)

<br />

***

<br />

아무튼, VMWare를 실행하셨으면, 저 버튼을 눌러서

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/4.png)

<br />
가상머신을 추가해주세요. 전 `High Sierra`를 설치할 예정인지라, 버전을 `10.13`으로 했어요.

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/5.png)

<br />
가상머신 이름 적당히 입력 후에, 가상 디스크 용량도 적당히 입력

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/6.png)

<br />
`Customize Hardware`를 눌러서

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/7.png)

<br />
이 화면을 열 수 있는데, 만약 이 화면이 열리지 않는다면, 일단 `Finish` 버튼 눌러서 가상머신 추가를 끝낸 뒤에,

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/8.png)

<br />
마우스 오른쪽 클릭해서 `Settings`를 누르면 되는거에요.

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/9.png)

<br />
아무튼 전 적당히 사양을 수정했어요.

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/10.png)

<br />
그리고 저 부분을 눌러서

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/11.png)

<br />
능력것 찾아온 High Sierra .iso 파일을 선택해주세요.

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/12.png)

<br />
가상머신을 실행하면 사과가 나오고

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/13.png)

<br />
부팅이 시작될거에요.

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/14.png)

<br />
언어는 일단

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/15.png)

<br />
한국어로 골랐어요.

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/16.png)

<br />
`디스크 유틸리티` 실행

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/17.png)

<br />
그려면 나오는 이 화면에서

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/18.png)

<br />
모든 기기 보기를 누르면

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/19.png)

<br />
아까 추가했던 가상 디스크를 찾을 수 있을거에요. 상단 중앙에 보이는 지우기 버튼을 눌러서

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/20.png)

<br />
디스크 초기화를 해주세요.

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/21.png)

<br />
끝

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/22.png)

<br />
이제 끝났으니 종료

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/23.png)

<br />
`macOS 설치`를 눌러서 설치를 시작하면

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/24.png)

<br />
어라

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/25.png)

<br />
저건 시간을 과거로 돌리면 해결되니, 일단 macOS 설치를 종료한뒤에, 터미널을 열고

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/26.png)

<br />
`date 0920092019` 입력. 그러면 시간이 과거로 설정될거에요.

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/27.png)

<br />
아무튼 터미널 종료

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/28.png)

<br />
인터넷에 연결해두면 저절로 다시 원래 시간으로 바뀔 수도 있으니, 인터넷 연결도 끊어보시는 것을 추천해요.

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/29.png)

<br />
다시 `macOS 설치`를 눌러서 설치를 시작하면,

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/30.png)

<br />
이번에는 설치가 잘 될거에요.

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/31.png)

<br />
동의

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/32.png)

<br />
아까 초기화했던 가상 디스크 선택 후 설치 시작

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/33.png)

<br />
다시 사과

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/34.png)

<br />
남은 시간 알려주는거 그짓말이니 믿지 마세요.

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/35.png)

<br />
설치가 끝나면 나라 선택 화면이 나와요.

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/36.png)

<br />
대한민국 선택

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/37.png)

<br />
키보드는 한국어 두벌식

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/38.png)

<br />
전 백업할 데이터는 없고 애플 아이디도 사용하지 못하니 둘 다 패스

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/39.png)

<br />
건너뜀!

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/40.png)

<br />
약관 동의해주시고

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/41.png)

<br />
이건 PC 로그인에 사용할 계정 생성이에요.

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/42.png)

<br />
계속

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/43.png)

<br />
시간대는 서울로 설정하고, 분석 정보 보내는건 전 전부 다 체크 해제했어요.

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/44.png)

<br />
그리고 조금 기다리면

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/45.png)

<br />
macOS가 나올거에요.

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/46.png)

<br />
설치 끝!

![image]({{site.url}}{{site.baseurl}}/assets/images/vmware-macos/47.png)
