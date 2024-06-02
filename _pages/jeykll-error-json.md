---
layout: post
title: "Jeykll 테마 cannot load such file -- json 오류 해결"
featured-img: jeykll-error-json.png
---

해결 방법 요약 : `Gemfile`에 `gem "json"` 추가


아니, 오랜만에 블로그에 글을 올리려고 하는데, `bundle exec jeykll serve` 명령어를 입력했는데, 오류가 뜨는거에요.
```sh
/usr/...(중략).../jekyll.rb:29:in 'require': cannot load such file -- json (LoadError)
```

![image]({{site.url}}{{site.baseurl}}/assets/images/thumb/jeykll-error-json.png)

<br/>
`json`이라는 `gem`이 없다는 내용이니, `gem install json`명령어를 통해 설치했어요. 근데 자꾸 없다고 나와요.

전 `jekyll serve` 명령어가 아니라 `bundle exec jekyll serve` 명령어로 홈페이지를 실행하고 있었는데, 뭔가 이게 원인인 것 같다는 생각이 들었어요. <br />
`gem list json` 명령어를 사용하면 `json`이라는 `gem`이 2개나 깔려있다고 뜨는데, `bundle exec gem list json` 명령어를 사용하면 하나도 없다고 떠요. 그래서 이번에는 `bundle exec install json`으로 깔아봤어요.


![image]({{site.url}}{{site.baseurl}}/assets/images/jeykll-error-json/0.png)

<br/>
새로운 `gem`이 설치되었다고 뜨긴 했는데, 문제는 그래도 `'require': cannot load such file -- json` 오류가 사라지지 않고, `bundle exec gem list json` 명령어를 사용하면 아무것도 없다고 떠요.

근데, 인터넷을 뒤적거려보니 그냥 `Gemfile`에 `gem "json"` 추가하면 된다는 내용이 보이더라구요. 따라해보니 아주 잘 켜지네요.

![image]({{site.url}}{{site.baseurl}}/assets/images/jeykll-error-json/1.png)

<br/>
`Gemfile` 파일은 `jeykll 테마를 사용하는 프로젝트` 폴더에 들어있을거에요.