---
layout: post
title: "IDE 없이 자바 스프링부트 개발하기"
featured-img: java-springboot.png
---

자바 `스프링부트` 개발을 위해 `이클립스`나 `인텔리제이` 등 IDE를 설치하거나, `Visual Studio Code`에 확장팩을 설치하여 사용하는 경우가 많이 보이는데, 굳이 그럴 필요가 없어요.

사실 `메모장`과 `cmd`만 있다면 충분히 가능해요. 리눅스 환경이라면 `vim` 같은 것을 사용해서, 터미널 창 하나만 띄워두고도 가능.
하지만 전 그 정도 변태는 아니기 때문에, 평소에 사용하던 `Visual Studio Code`를 사용할거에요. 물론 확장팩은 단 하나도 설치하지 않을 예정

이것저것 오류가 나는 관계로, 그냥 싹 다 구버전으로 내렸어요. 제 환경은 다음과 같아요.
```
운영체제 : 리눅스 (아치 리눅스)
Java 버전 : 11
JDK 종류 : OpenJDK
스프링부트 버전 : 2.7.3
```

***
## Open JDK 11 설치

저는 `아치 리눅스`를 사용하고 있기 때문에, 그냥 `pacman`으로 설치하면 끝.
일단 `pacman -sS java | grep jdk11` 명령어를 통해 패키지 확인 후, `pacman -S jdk11-openjdk` 명령어로 설치했어요.

```sh
$ sudo pacman -S jdk11-openjdk
```

![image]({{site.url}}{{site.baseurl}}/assets/images/java-springboot/0.png)

<br/>
`우분투` 같은 경우는 다음과 같은 명령어를 사용하시면 될 것이고, 다른 `리눅스`라면 그에 맞는 패키지 관리자를 통해 설치하시면 돼요.
`리눅스`를 사용하여 개발하는 사람이라면, 그 정도는 스스로 할 수 있는 실력이 될 듯
```sh
$ sudo apt install openjdk-11-jdk 
```

`macOS`를 쓰신다면 `brew` 명령어 등을 통해 설치 가능. `윈도우`를 사용하신다면 [여기서](https://jdk.java.net/java-se-ri/11) 윈도우용으로 받아서 적당한 곳에 압축 해제 후 환경 변수 설정 등을 하시면 돼요.

`javac` 명령어와 `java` 명령어가 아주 잘 실행되는 것으로 보아 환경변수 설정은 알아서 되거나, 과거의 내가 해놓은 듯 해요.

![image]({{site.url}}{{site.baseurl}}/assets/images/java-springboot/1.png)

***
## 스프링부트 프로젝트 생성

[https://start.spring.io/](https://start.spring.io/)에 접속해서 이것저것 알아서 입력하고 `GENERATE` 버튼을 누르면 스프링부트 프로젝트가 생성되어 `.zip 파일`로 다운로드될거에요.
메타데이터는 `Group` 항목 등에 입력하면 패키지명이 어떻게 알아서 입력되는지 등을 보면서 알아서 적고, 나머지는 그대로 두면 되는거에요.

![image]({{site.url}}{{site.baseurl}}/assets/images/java-springboot/2.png)

<br/>
어차피 전 `gradle`과 `java`를 사용하고 `.jar`로 배포할 예정이며, 나머지는 다 수정할거라 그냥 두고 생성했어요.

아무튼 `.zip 파일`의 압축을 풀고 원하는 편집기로 열어주세요.

![image]({{site.url}}{{site.baseurl}}/assets/images/java-springboot/3.png)

***
## 실행 전 이것저것 수정

전 위에서 언급한 것처럼 `vs code(Visual Studio Code)`로 열었어요. `README.md`가 있는 이유는 깃허브 레포 폴더에 압축을 풀어놓고 열었기 때문

![image]({{site.url}}{{site.baseurl}}/assets/images/java-springboot/4.png)

<br/>
`build.gradle` 파일의 내용을 다음과 같이 수정해주세요. 다음 사진에서 주석 처리되어있는 부분을 그 아래에 적은 내용처럼 수정해주세요.

![image]({{site.url}}{{site.baseurl}}/assets/images/java-springboot/5.png)

***
## 스프링부트 프로젝트 실행

`./gradlew bootRun` 명령어를 통해 실행할 수 있어요. 최최 실행이라 그런지 이것저것 많이 받네요.
실행 중인 명령어는 `Ctrl + C`로 끌 수 있어요.

![image]({{site.url}}{{site.baseurl}}/assets/images/java-springboot/6.png)

<br/>

`스프링부트`의 기본 포트는 `8080`이니 웹 브라우저에서 `http://localhost:8080`을 입력하면 `지금 내 컴퓨터에서 실행 중이고 내 컴퓨터에서만 접속할 수 있는 자바 스프링부트로 실행된 서버`에 접속할 수 있어요.
아직 아무것도 안넣어서 404가 뜨는 중

![image]({{site.url}}{{site.baseurl}}/assets/images/java-springboot/7.png)

***
## Hello World 예제

`어쩌고Controller.java`와 같은 형식인 파일 생성 후 대충 다음과 같은 내용을 적어주세요. 본인이 진행하려는 프로젝트의 이름에 맞게 지으시면 되는거에요.

```java
package com.본인프로젝트의.패키지명;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class 어쩌고Controller {

    @GetMapping("/")
    public String getHelloWorld() {
        return "Hello World";
    }

}
```

<br/>
다시 실행한 모습. 스프링부트로 실행시킨 서버에 접속하니 `Hello World`가 잘 나오네요.

![image]({{site.url}}{{site.baseurl}}/assets/images/thumb/java-springboot.png)