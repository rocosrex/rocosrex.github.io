---
title: "Internationalization"
date: 2022-11-30 13-00-00 +0900
toc: true
toc_sticky: true
toc_label: 바로 가기 목차
categories: Flutter
---
Flutter의 Internationaliztion에 대해 고찰해 보겠다.



**참고자료:**

Flutter 공식 문서: [공식 문서](<https://docs.flutter.dev/development/accessibility-and-localization/internationalization>)
공부하는 홍짜: <https://lovelyhongjja.tistory.com/7>
대부류: <https://devuryu.tistory.com/401>
Just try it!: <https://moonsiri.tistory.com/>



### Globalization vs Internationalization vs Localization [[1]](#참조-1)

이 기능을 구현하기 위해 여기저기 구글링하다보니 조금 헷갈리는 용어들이 있어서, 찾아보면서 느낀 용어들의 정의를 여기서 정리하고 가고자 한다.

  - Globalization : application을 여러 언어, 여러 국가에서도 사용 가능하도록 만드는  complete한 과정을 말한다.  Localization과 Internationalization의 상위 개념으로, 기능 구현에서 벗어난, 좀 더 포괄적인 느낌이다.
  - Internationalization : application을 여러 언어, 여러 국가에서도 사용 가능하도록 지원한다. 언어를 번역해주고, 시간을 설정하는 등 여러 기능이 포함될 수 있다.
  - Localization : application을 여러 언어로 사용이 가능하도록 여러 언어를 지원(번역)해주는 기능을 말한다.

이 포스트에서 설명할 기능은 단순히 언어를 번역해주는 단순한 기능이기 때문에, 이 기능은 이하 **Localization**이라고 칭하기로 한다.



### 지원하는 Package[[2]](#참조-2)
지원하는 패키지는

  - **[intl](https://pub.dev/packages/intl/versions/0.16.1)** : dart에서 internalization and localization를 지원하는 패키지로서 다국어 처리나 성별, 날짜, 숫자 등을 그 지역이나 국가에 맞게 바꿀 때 사용
  - **[flutter_i18n](https://pub.dev/packages/flutter_i18n)** : 유지보수 중단
  - **[easy_localization](https://pub.dev/packages/easy_localization)** : key:value 형식을 사용



### Internationalization 절차-**[intl](https://pub.dev/packages/intl/versions/0.16.1)** 사용



#### 1.  `pubspec.yaml` 에 pacakge 추가

~~~yaml
dependencies:
  flutter:
    sdk: flutter
  flutter_localizations: # Add this line
    sdk: flutter         # Add this line
  intl: ^0.17.0 # Add this line
~~~

추가된 pacakage를 설치하기 위해 pub get 실행한다.

#### 2. generate 추가

```yaml
# The following section is specific to Flutter.
flutter:
  generate: true # Add this line
```

#### 3. 새로운 l10n.yaml  파일 추가 (root directory)

```
arb-dir: lib/l10n
template-arb-file: app_en.arb
output-localization-file: app_localizations.dart
```



![image-20221130163358917](https://raw.githubusercontent.com/rocosrex/rocosrex.github.io/main/assets/images/blogimage-20221130163358917.png)



#### 4. `app_en.arb`, app_ko.arb template file 추가

.arb 파일은 구글에서 만든 Application Resource Bundle이다.

프로젝트 ${FLUTTER_PROJECT}/lib/l10n에 `app_en.arb` template file 추가

```
{
    "helloWorld": "Hello World!",
    "@helloWorld": {
      "description": "The conventional newborn programmer greeting"
    }
}
```

프로젝트 ${FLUTTER_PROJECT}/lib/l10n에 `app_ko.arb` template file 추가

```
{
    "helloWorld": "안녕하세요!"
}
```

#### 5. run `flutter gen-l10n` at Terminal

![image-20221130164546769](https://raw.githubusercontent.com/rocosrex/rocosrex.github.io/main/assets/images/blogimage-20221130164546769.png)

.dart_too/flutter_gen/genI10n directory에 localizations 관련 파일이 3개 생긴다.

- app_localizations.dart

- app_localizations_en.dart
- app_localizations_ko.dart



#### 6. main.dart에 internationlization 관련 코드 수정

```
import 'package:flutter_gen/gen_l10n/app_localizations.dart';
```

```
return const MaterialApp(
  title: 'Localizations Sample App',
  localizationsDelegates: [
    AppLocalizations.delegate, // Add this line
    GlobalMaterialLocalizations.delegate,
    GlobalWidgetsLocalizations.delegate,
    GlobalCupertinoLocalizations.delegate,
  ],
  supportedLocales: [
    Locale('en', ''), // English, no country code
    Locale('es', ''), // Spanish, no country code
  ],
  home: MyHomePage(),
);
```

GlobalMaterialLocalizations.delegate 라인에 빨간줄 에러가 생긴다. 아래 import code가 없어서 발생한다.

```
import 'package:flutter_gen/gen_l10n/app_localizations.dart';
```



![image-20221130165707357](https://raw.githubusercontent.com/rocosrex/rocosrex.github.io/main/assets/images/blogimage-20221130165707357.png)



####7. 사용하기



```
class _MyHomePageState extends State<MyHomePage> {
  int _counter = 0;

  void _incrementCounter() {
    setState(() {
      _counter++;
    });
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text(widget.title),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[
            Text(AppLocalizations.of(context)!.helloWorld),
            const Text(
              'You have pushed the button this many times:',
            ),
            Text(
              '$_counter',
              style: Theme.of(context).textTheme.headline4,
            ),
          ],
        ),
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: _incrementCounter,
        tooltip: 'Increment',
        child: const Icon(Icons.add),
      ), // This trailing comma makes auto-formatting nicer for build methods.
    );
  }
}
```



- 영문 결과

![image-20221130170738428](https://raw.githubusercontent.com/rocosrex/rocosrex.github.io/main/assets/images/blogimage-20221130170738428.png)



**Phone의 시스템 셋팅에서 언어를 변경한다.**



- 한글 결과

![image-20221130170429442](https://raw.githubusercontent.com/rocosrex/rocosrex.github.io/main/assets/images/blogimage-20221130170429442.png)



#### 8. device app description에 적용하기

```
return MaterialApp(
  onGenerateTitle: (context) =>
      DemoLocalizations.of(context).title,
```

MaterialApp의 title은 어디에 쓰이는가?

- Useful for the Android only.

- On iOS this value cannot be used.

안드로이는 최근 사용앱에 표시되고, IOS에는 사용되지 않는다.



### Localizing for iOS: Updating the iOS app bundle

##### 1. Open your project’s `ios/Runner.xcworkspace` Xcode file.

![1](https://raw.githubusercontent.com/rocosrex/rocosrex.github.io/main/assets/images/blog1.png)



##### 2. open the `Info.plist` file under the `Runner` project’s `Runner` folder. Select the **Information Property List** item. Then select **Add Item** from the **Editor** menu, and select **Localizations** from the pop-up menu. 아래 화면은 이미 추가된 화면이다.

![2](https://raw.githubusercontent.com/rocosrex/rocosrex.github.io/main/assets/images/blog2.png)



##### 3. dart_too/flutter_gen/genI10n directory에 localizations 관련 파일 3개가 있는지 확인한다. 없으면 터미널에서 `flutter gen-l10n`를 실행 한다.

![3](https://raw.githubusercontent.com/rocosrex/rocosrex.github.io/main/assets/images/blog3.png)



##### 4. IOS에 적용된 결과

<img src="https://raw.githubusercontent.com/rocosrex/rocosrex.github.io/main/assets/images/blog4.png" alt="4" style="zoom: 25%;" />







끝...




### 참조 자료
 - 참조 1:  <https://devuryu.tistory.com/401> 
 - 참조 2: <https://moonsiri.tistory.com/83> 
