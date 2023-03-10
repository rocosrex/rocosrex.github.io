---
title: "Firebase Auto 고찰"
date: 2022-12-01 13-00-00 +0900
categories: firebase
---
Firebase Authentication에 관한 고찰이다.



#1. dependencies

```
dependencies:
  flutter:
    sdk: flutter


  # The following adds the Cupertino Icons font to your application.
  # Use with the CupertinoIcons class for iOS style icons.
  cupertino_icons: ^1.0.2
  firebase_core: ^2.3.0
  firebase_auth: ^4.1.4
```



#2. main.dart

```
import 'package:flutter/material.dart';
import 'package:firebase_core/firebase_core.dart';

void main() {
  WidgetsFlutterBinding.ensureInitialized();
  runApp(const MyApp());
}
```
