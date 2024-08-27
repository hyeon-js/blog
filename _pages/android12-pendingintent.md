---
layout: post
title: "Android 12 이상에서 PendingIntent 사용시 오류"
featured-img: android12-pendingintent.png
---

카드 잔액 확인 앱을 만드는데, 비교적 최근에 출시된 기기에서 앱실행시키니 바로 종료되어버렸어요. 알고보니, `PendingIntent`를 생성하는 부분에서 `java.lang.IllegalArgumentException`가 발생하고 있었어요.

이럴 때는 Flag로 `FLAG_IMMUTABLE`나 `FLAG_MUTABLE`를 넣어주면 되는거예요.

```java
import android.app.PendingIntent;
.
.
.
PendingIntent pi = PendingIntent.getActivity(this, 0, intent, PendingIntent.FLAG_IMMUTABLE);
//또는
PendingIntent pi = PendingIntent.getActivity(this, 0, intent, PendingIntent.FLAG_MUTABLE);
```


그리고, `FLAG_IMMUTABLE`은 `API 레벨 23(안드로이드 6.0)`에서, `FLAG_MUTABLE`은 `API 레벨 31(안드로이드 12)`에서 추가되었기 때문에, if문 등으로 나눠서 처리해야 해요.