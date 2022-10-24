---
title: "크기 구하기 Tip"
date: 2022-10-18
template: main.html
---

## kToolbarHeight
Appbar의 사이즈를 구함.
```dart
margin: EdgeInsets.only( // (1)
                top: kToolbarHeight),
```

1. 적용전 <br><br>![kToolbarBar_before](/docs/assets/img/flutter/Theory/scrollable_widget/kToolBar_before.png)<br>
적용후<br><br>![kToolbarBar_after](/docs/assets/img/flutter/Theory/scrollable_widget/kToolBar_after.png)

## 화면 전체 사이즈
```dart
MediaQuery.of(context).size.width // 가로
MediaQuery.of(context).size.height // 세로
```

## 키보드 사이즈 
여기에다가 높이 더 해주면 키보드 올라오면 키보드 크기만큼 높이 올라감.
```dart
final bottomInsets = MediaQuery.of(context).viewInsets.bottom;
```
