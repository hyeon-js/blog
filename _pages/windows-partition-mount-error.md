---
layout: post
title: "리눅스에서 갑자기 윈도우 파티션이 마운트되지 않을 때"
featured-img: windows-partition-mount-error.png
---

아무것도 안했는데 갑자기 `윈도우가 설치된 파티션`을 리눅스에서 마운트하지 못하는 경우가 있어요.
근데, 사실 가만 생각해보면 윈도우로 부팅된 상태에서 강제 종료 등을 했을지도 몰라요.

![image]({{site.url}}{{site.baseurl}}/assets/images/windows-partition-mount-error/0.png)

<br/>

그럴 때는 그냥 윈도우로 부팅한 후에, `윈도우가 설치된 파티션`의 오류 검사를 해주면 마운트가 될거에요.

![image]({{site.url}}{{site.baseurl}}/assets/images/windows-partition-mount-error/1.png)

<br/>

전 `윈도우가 설치된 파티션 (C 드라이브)`에서 잠재적인 오류가 있다고 떴어요.

![image]({{site.url}}{{site.baseurl}}/assets/images/thumb/windows-partition-mount-error.png)

<br/>

윈도우로 부팅한 상태라는 것은 현재 해당 `파티션(드라이브)`를 사용 중이라는 뜻이기 때문에, 오류 수정 등이 불가능해요.
저기서 다시 시작 및 복구 같은걸 선택하면 컴퓨터가 재부팅되는 시점에 알아서 오류를 수정할거에요.

![image]({{site.url}}{{site.baseurl}}/assets/images/windows-partition-mount-error/2.png)

<br/>

이제 리눅스로 부팅해서 마운트를 시도해보면 아주 잘 될 거에요.
