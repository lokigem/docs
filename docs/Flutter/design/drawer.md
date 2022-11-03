---
title: "Drawer"
date: 2022-10-15
template: main.html
---

왼쪽에서 BottomSheet나 SnackBar처럼 화면을 덮으면서 나오는 창. Scaffold 안에 넣어주기만 하면 바로 나타남.
```dart
Scaffold(
    drawer: Drawer(
        child: ,
    )
)
```
<center>ㅏ
![drawer](/docs/assets/img/flutter/Theory/drawer/drawer.gif){: width="50%" }
</center>

## drawer 닫는 방법
drawer도 하나의 화면으로 취급하기 때문에, 
```dart
Navigation.of(context).pop();
```
으로 닫아줄 수 있음.
