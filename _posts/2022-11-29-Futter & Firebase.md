---
title: "Flutter & Firebase"
date: 2022-11-29 11-29-00 +0900
categories: Git 
---
Flutter에 Firebase를 사용하기 위한 절차를 기술하고자 한다. 본 기술은 윈도우 기준이다.



[Firebase  공식 guide]: https://firebase.google.com/docs/flutter/setup?hl=ko&amp;platform=ios



##### 1. [Firebase에 login](https://console.firebase.google.com/?hl=ko) 한다. 구글 계정이 있으면 가입절차 없이 로그인 되는 것 같다.

<img src="https://raw.githubusercontent.com/rocosrex/rocosrex.github.io/main/assets/images/blogimage-20221129103238859.png" alt="image-20221129103238859" style="zoom: 33%;" />



##### 2. [Firebase CLI ](https://firebase.google.com/docs/cli?hl=ko#setup_update_cli)를 설치 한다.

<img src="https://raw.githubusercontent.com/rocosrex/rocosrex.github.io/main/assets/images/blogimage-20221129104611185.png" alt="image-20221129104611185" style="zoom: 50%;" />

이 작업은 firebase-tools-instant-win.exe 를 다운로드 하는 것이다. 따로 설치 파일이 없다.

이 파일을 Flutter Project folder가 있는 폴더에 놓고 사용해야 한다. 

<img src="https://raw.githubusercontent.com/rocosrex/rocosrex.github.io/main/assets/images/blogimage-20221129105129829.png" alt="image-20221129105129829" style="zoom: 50%;" />



3. Firebase 로그인 및 테스트

comman prompt를 실행 한 후,  firebase-tools-instant-win.exe가 있는 폴더로 이동하여 실행 시킨다.

