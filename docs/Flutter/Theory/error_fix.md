---
title: "Error Fix"
date: 2022-11-08
template: main.html
---

## MultiDex Error 
빌드 할 때 생기는 Error 안드로이드에서만 발생함, 큰 앱을 빌들하려면 MultiDex를 활성화 시켜줘야 한다는데 이를 수동으로 활성화 시켜주는 방법임.
```gradle title="/app/build.gradle"
defaultConfig {
    ...
    multiDexEnabled true
}
```

<br>and<br>

```gradle title="/app/build.gradle"
dependencies {
    ...
    implementation 'com.android.support:multidex:1.0.3'
}
```

### reference
[stack overflow](https://stackoverflow.com/questions/49886597/multidex-issue-with-flutter)<br>