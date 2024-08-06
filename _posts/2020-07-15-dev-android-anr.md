---  
layout: post  
title: "[Android] 앱 종료 후 재시작 시에 튕김, 비정상 종료 될 때"  
subtitle: "Android"  
categories: dev
tags: Dev Android 기술 안드로이드 ANR
comments: true  
header-img: null
---  

앱 개발 도중 앱 실행 중에 종료 후, 다시 시작할 때 튕기는 현상이 있었다. 로그인을 한 후에 재 시작했을 때 발생해서
로그인 관련 문제인가 싶어 시도 해보다가, 앱이 완전히 종료되지 않아서 발생하는게 아닌가 싶어서 시도 해 봤는데,
완전히 종료된게 아니기 때문에 발생한게 맞는 듯 싶다.

```java
@Override
public void onBackPressed() { // DrawerLayout 이 열려있을 경우에는 DrawerLayout을 닫는다
        DrawerLayout drawer = findViewById(R.id.drawer_layout);
        if (drawer.isDrawerOpen(GravityCompat.END)) {
            drawer.closeDrawer(GravityCompat.END);
        } else {
            if(getSupportFragmentManager().getBackStackEntryCount() == 0)
            {
                moveTaskToBack(true); // 백그라운드로 전환
                finishAndRemoveTask();
                android.os.Process.killProcess(android.os.Process.myPid());
            }else
            {
               super.onBackPressed();
            }
        }
    }
```

주목 할 부분은 else 문 안에 if문 쪽이다. 나 같은 경우는 프래그먼트를 사용 했기 때문에, 만약에 프래그먼트가 메인 화면의 프래그먼트 일 경우(스택에 저장된 프래그먼트가 더이상 없을 경우) 앱을 완전히 종료하고, 아닐 경우는 backPressed를 실행 하도록 했다. 앱을 완전히 종료하고 나니 재 시작 했을 때도 튕기는 현상이 없어졌다!