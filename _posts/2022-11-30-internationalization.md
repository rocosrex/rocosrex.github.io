---
title: "Internationalization"
date: 2022-11-30 13-00-00 +0900
categories: Flutter
---
Flutter의 Internationaliztion에 대해 고찰해 보겠다.



참고자료:

Flutter 공식 문서: <https://docs.flutter.dev/development/accessibility-and-localization/internationalization>

공부하는 홍짜: <https://lovelyhongjja.tistory.com/7>

대부류: <https://devuryu.tistory.com/401>

Just try it!: <https://moonsiri.tistory.com/>



## Globalization vs Internationalization vs Localization [1](#참조1)

이 기능을 구현하기 위해 여기저기 구글링하다보니 조금 헷갈리는 용어들이 있어서, 찾아보면서 느낀 용어들의 정의를 여기서 정리하고 가고자 한다.

- - Globalization : application을 여러 언어, 여러 국가에서도 사용 가능하도록 만드는  complete한 과정을 말한다.  Localization과 Internationalization의 상위 개념으로, 기능 구현에서 벗어난, 좀 더 포괄적인 느낌이다.
  - Internationalization : application을 여러 언어, 여러 국가에서도 사용 가능하도록 지원한다. 언어를 번역해주고, 시간을 설정하는 등 여러 기능이 포함될 수 있다.
  - Localization : application을 여러 언어로 사용이 가능하도록 여러 언어를 지원(번역)해주는 기능을 말한다.

이 포스트에서 설명할 기능은 단순히 언어를 번역해주는 단순한 기능이기 때문에, 이 기능은 이하 **Localization**이라고 칭하기로 한다.



[1]:  <https://devuryu.tistory.com/401>
