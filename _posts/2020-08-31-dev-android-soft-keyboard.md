---  
layout: post  
title: "[Android] 소프트키보드가 레이아웃에 영향을 줄 때"  
subtitle: "Android"  
categories: dev
tags: Dev Android 기술 안드로이드 SoftKeyboard Layout
comments: true  
header-img: null
---  

앱 개발을 하던 도중에 EditText에 포커스가 가면 레이아웃 크기가 작아지는 현상이 발생했다. 
문제는 EditText에 포커스가 갈 때 올라오는 소프트 키보드가 레이아웃에 영향을 끼쳐서 크기가 작아지는 것 이었다.

Manifest 파일에서 문제가 생기는 해당 액티비티 내에 아래의 옵션을 주면 키보드가 해당 액티비티의 레이아웃에
영향을 끼치지 않았다.

```xml
android:windowSoftInputMode="adjustNothing"
```