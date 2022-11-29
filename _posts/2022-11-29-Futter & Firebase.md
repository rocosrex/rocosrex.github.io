---
title: "Flutter & Firebase"
date: 2022-11-29 11-29-00 +0900
categories: Git 
---
Flutter에 Firebase를 사용하기 위한 절차를 기술하고자 한다. 본 기술은 윈도우 기준이다.



[Firebase  공식 guide]: https://firebase.google.com/docs/flutter/setup?hl=ko&amp;platform=ios



##### 1.   [Firebase에 login](https://console.firebase.google.com/?hl=ko) 한다. 구글 계정이 있으면 가입절차 없이 로그인 되는 것 같다.

<img src="https://raw.githubusercontent.com/rocosrex/rocosrex.github.io/main/assets/images/blogimage-20221129103238859.png" alt="image-20221129103238859" style="zoom: 33%;" />



##### 2. [Firebase CLI ](https://firebase.google.com/docs/cli?hl=ko#setup_update_cli)를 설치 한다.

<img src="https://raw.githubusercontent.com/rocosrex/rocosrex.github.io/main/assets/images/blogimage-20221129104611185.png" alt="image-20221129104611185" style="zoom: 50%;" />

이 작업은 firebase-tools-instant-win.exe 를 다운로드 하는 것이다. 따로 설치 파일이 없다.

이 파일을 Flutter Project folder가 있는 폴더에 놓고 사용해야 한다. 

<img src="https://raw.githubusercontent.com/rocosrex/rocosrex.github.io/main/assets/images/blogimage-20221129105129829.png" alt="image-20221129105129829" style="zoom: 50%;" />



##### 3. Firebase 로그인 및 테스트

- firebase-tools-instant-win.exe 실행

comman prompt를 실행 한 후,  firebase-tools-instant-win.exe가 있는 폴더로 이동하여 실행 시킨다. 아래와 같이 welcome to.. firebase 로고가 나온 후, 명령 입력 대기 상태가 된다.

<img src="https://raw.githubusercontent.com/rocosrex/rocosrex.github.io/main/assets/images/blogimage-20221129110744894.png" alt="image-20221129110744894" style="zoom:50%;" />

- firebase 로그인

```
firebase login --interactive
```

만약 이미 로그인 되어 있다면 아래와 같이 결과가 나타난다. 참고로 로그아웃 명령은 firebase logout 이다. 지금은 하지 않는다.

```
> firebase login --interactive
Already logged in as 여러분의email
```

로그인 되어 있지 않다면 다음 화면과 같이 인터넷 브라우저에서 로그인 할 수 있는 화면이 나오고 여기서 로긴을 한다.

<img src="https://raw.githubusercontent.com/rocosrex/rocosrex.github.io/main/assets/images/blogimage-20221129112518503.png" alt="image-20221129112518503" style="zoom: 67%;" />

여기서, 'Y'키를 클릭 후, 엔터하면,

<img src="https://raw.githubusercontent.com/rocosrex/rocosrex.github.io/main/assets/images/blogimage-20221129112616802.png" alt="image-20221129112616802" style="zoom:67%;" />

위 화면이 나오고, 인터넷 브라우저에 로그인 화면이 나타나며, 로그인을 기다린다는 메세지가 나타난다.

<img src="https://raw.githubusercontent.com/rocosrex/rocosrex.github.io/main/assets/images/blogimage-20221129113020694.png" alt="image-20221129113020694" style="zoom:67%;" />

인터넷 브라우저에서 로그인을 한다. 2차 계정 보호가 되어 있는 분은 2차 확인까지 해 준다.

<img src="https://raw.githubusercontent.com/rocosrex/rocosrex.github.io/main/assets/images/blogimage-20221129113207627.png" alt="image-20221129113207627" style="zoom:67%;" />

Firebase CLI 앱을 신뢰할 수 있는지 확인해 달라고 하는데, '허용' 버튼을 클릭한다.

<img src="https://raw.githubusercontent.com/rocosrex/rocosrex.github.io/main/assets/images/blogimage-20221129113302409.png" alt="image-20221129113302409" style="zoom:67%;" />

Firebase CLI 로그인이 성공 했다는 화면이 나온다. 이제 인터넷 브라우저를 종료해도 된다.

Firebase CLI 콘솔화면에도 인증에 성공했다는 메세지가 나타난다.

<img src="https://raw.githubusercontent.com/rocosrex/rocosrex.github.io/main/assets/images/blogimage-20221129113441275.png" alt="image-20221129113441275" style="zoom:67%;" />

firebase 프로젝트 리스트 보기를 실행하여, 계정에 억세스 가능한지 테스트한다.

<img src="https://raw.githubusercontent.com/rocosrex/rocosrex.github.io/main/assets/images/blogimage-20221129113549393.png" alt="image-20221129113549393" style="zoom:67%;" />

이미 firebase에 프로젝트를 만들었던 사람은 프로젝트 리스트가 나오겠지만, 처음인 사람은 프로젝트가 없다는 메세지가 나온다.



##### <!--4. Google Cloud Flatform 약관 동의-->



<!--<img src="https://raw.githubusercontent.com/rocosrex/rocosrex.github.io/main/assets/images/blogimage-20221129133912734.png" alt="image-20221129133912734" style="zoom: 25%;" />-->

<!--모두 동의하고 '동의 및 계속하기' 를 클릭한다.-->

<!--<img src="https://raw.githubusercontent.com/rocosrex/rocosrex.github.io/main/assets/images/blogimage-20221129134012112.png" alt="image-20221129134012112" style="zoom:25%;" />-->





<!--<img src="https://raw.githubusercontent.com/rocosrex/rocosrex.github.io/main/assets/images/blogimage-20221129134053619.png" alt="image-20221129134053619" style="zoom:25%;" />-->

<!--오른쪽 위 '활성화' 버튼 클릭-->

<!--<img src="https://raw.githubusercontent.com/rocosrex/rocosrex.github.io/main/assets/images/blogimage-20221129134343606.png" alt="image-20221129134343606" style="zoom:25%;" />-->



<!--'계속' 버튼 클릭-->

##### 3. 프로젝트 생성

<img src="https://raw.githubusercontent.com/rocosrex/rocosrex.github.io/main/assets/images/blogimage-20221129135030881.png" alt="image-20221129135030881" style="zoom: 33%;" />





<img src="https://raw.githubusercontent.com/rocosrex/rocosrex.github.io/main/assets/images/blogimage-20221129135052492.png" alt="image-20221129135052492" style="zoom:33%;" />



#####4.  firebase 프로젝트 생성

firebase에 프로젝트를 생성해야 한다. 여기서 프로젝트명은 전세계에서 유일한 이름을 가져야 한다고 한다. 프로젝트 이름 지정 제약은 다음과 같다.

- 길이: 4~30자

- 문자, 숫자, 공백, -, ', ", !만 사용

- 영어 문자만 사용    

```
> firebase projects:create 프로젝트 이름
```

아래와 같이 프로젝트를 생성한다.

```
> filebase projects:create firebase-study-project-rex
```

project ID로 사용할 것인지 묻는다. 그냥 엔터키 누른다.

```
> firebase projects:create firebase-study-project-rex
? What would you like to call your project? (defaults to your project ID)
```



<img src="https://raw.githubusercontent.com/rocosrex/rocosrex.github.io/main/assets/images/blogimage-20221129135721102.png" alt="image-20221129135721102" style="zoom: 67%;" />



firebase console에서 확인해보면 다음과 같다. 프로젝트가 잘 생성이 되었다.



<img src="https://raw.githubusercontent.com/rocosrex/rocosrex.github.io/main/assets/images/blogimage-20221129135845961.png" alt="image-20221129135845961" style="zoom: 33%;" />


