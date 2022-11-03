---
title: "현재 scroll 위치 구하기"
date: 2022-10-18
template: main.html
---

## 구현하는 이유(활용)
```dart
스크롤이 일정이상 되면 동작하는 행위를 구현하기 위해서 // (1)
```

1. ![scrollListener](/docs/assets/img/flutter/Theory/scrollable_widget/scrollListener.gif)

## 구현

### ScollController() 선언
```dart
CrollController scrollController = ScrollController(); 
```

### scrollListner() {}
scrollListner로 동작할 함수 선언
```dart
scrollListener() {
    // 보이는 값 말고 실제 최상단에서 부터 현재 스크롤하는 위치까지의 간격
    // 500을 넘어가면 닫혀있는 상태
    bool isExpanded = scrollController.offset < 500 - kToolbarHeight;

    if(isExpanded != this.isExpanded) {
      setState(() {
        this.isExpanded = isExpanded;
      });
    }
  }
```
  
### initState에서 Contoller 추가
initState에서 scroller에 Listner 할당해줌
```dart
@override
initState() {
  super.initState();

  scrollController.addListener(scrollListener);
}
```

####  dispose()
initState에서 추가한 Listner들은 모두 dispose에서 모메리에서 해제시켜줘야 함
```dart
@override
dispose() {
    scrollController.removeListener(scrollListener);
    scrollController.dispose();

    super.dispose();
}
```

### ScrollView에 controller 추가
scrollView에서 동작할 controller 추가
```dart
CustomScrollView(
    ..., 
    controller: scrollController,
    ...,
):
```

## 참조
[미세먼지 프로젝트](https://github.com/rookedsysc/Flutter-Study/blob/a78c3cc8e8c45f825b5a2d7207e1520df1af5460/Project/dust_today/lib/screen/home_screen.dart)