---
title: "Scrollable Widget"
date: 2022-10-11
template: main.html
---

## Single Child Scroll View
기본은 스크롤이 안되지만, 화면이 길어지면 Scroll이 가능함.<br>
뷰를 호출할 때 전체 리스트를 한꺼번에 불러온다는 문제점이 있음. 이는 성능 이슈로 이어질 수 있음.
```dart
SingleChildScrollView(
  child: Column(
    children:
        rainbowColors.map((e) => RenderColorContainer(color: e)).toList(),
  ),
)
```
<center>
![renderSimple](/docs/assets/img/flutter/Theory/scrollable_widget/renderSimple.gif){: width="50%" }
</center>


### physics: 스크롤 스타일 
개체가 화면을 넘어가지 않으면 scroll이 불가능 하지만 이를 억지로 가능하게 해주는 방법도 있음. 
```dart
SingleChildScrollView(
  /* 
    Single Child ScrollView가 어떤 방식으로 작용하는지 정할 수 있음.
    AlwaysScrollableScrollPhysics() - 항상 스크롤 가능
    NeverScrollableScrollPhysics()- 절대 스크롤 불가능
    BouncingScrollPhysics() - iOS Style (튕김.)
    ClampingScrollPhysics() - Android Style (튕기지 않음.)
  */
  physics: AlwaysScrollableScrollPhysics(),
  child: Column(
    children: [
      RenderColorContainer(color: Colors.black),
    ],
  ),
);
```
<center>
![singgleViewScroll](/docs/assets/img/flutter/Theory/scrollable_widget/singleViewScroll.gif){: width="50%" }
</center>

#### clipBehavior: 화면 잘림
위에서 보면 화면이 스크롤 될 때 잘리는 것을 볼 수 있음. 이는 clipBehavior 속성을 추가해서 해결할 수 있음.
```dart
clipBehavior: Clip.none
```
전체 적용 👇
```dart
SingleChildScrollView(
  physics: AlwaysScrollableScrollPhysics(),
  // Clip.none : 화면 잘리지 않게 해줌.
  clipBehavior: Clip.none,
  child: Column(
    children: [
      RenderColorContainer(color: Colors.black),
    ],
  ),
);
```
<center>
![renderClip](/docs/assets/img/flutter/Theory/scrollable_widget/renderClip.gif){: width="50%" }
</center>

## List View
모든 뷰를 한 번에 보여주는 방법, 기본적인 사용 방법이지만 이는 위의 Single Child List View와 같이 성능 이슈로 이어질 가능성이 있음.
```dart
ListView (
  children: [
  ]
)
```
<center>
![ListView](/docs/assets/img/flutter/Theory/scrollable_widget/listView.gif){: width="50%" }
</center>

### Builder: Build되는 View만 생성
Build 되는 View만 생성하므로 성능 이슈 안정화.<br>
![listViewBuilder](/docs/assets/img/flutter/Theory/scrollable_widget/listViewBuilder.gif){: width="100%" }
```dart
ListView.builder(
  itemCount: 100,
  itemBuilder: (context, index) {
    print(index); // 새로운 뷰가 호출될 때마다 생성
    return RenderColorContainer(color: rainbowColors[index % rainbowColors.length],
      index: index,
    );
  },
);
```

### seperate: 사이사이에 view 생성
```dart
ListView.separated(
  itemBuilder: (context, index){
    return RenderColorContainer(
      // 랜더하고 싶은 뷰
      color: rainbowColors[index % rainbowColors.length]);   
    }, 
  separatorBuilder: (context, index){
    return RenderColorContainer(
      // 사이사이에 렌더하고 싶은 뷰
      color: Colors.black, 
      height: 50,
      );
    }, itemCount: 100);
}
```
<center>
![seperateRender](/docs/assets/img/flutter/Theory/scrollable_widget/seperateRender.gif){: width="50%" }
</center>

## Grid View
가로로 여러 개의 View를 표시할 수 있음.
### Count 
뷰를 한 번에 다 그려낸다는 단점이 있음.
```dart
crossAxisCount 
```
에 가로로 표시될 뷰의 갯수를 넣어줄 수 있음. 전체 코드 👇
```dart
GridView.count(
  crossAxisCount: 2, // 가로 뷰 갯수
  crossAxisSpacing: 12.0, // 가로 간격
  mainAxisSpacing: 12.0, // 가로 간격
  children: numbers
      .map(
        (e) => RenderColorContainer(
      color: rainbowColors[e % rainbowColors.length],
      index: e,
    ),
  ).toList(),
);
```
<center>
![renderCount](/docs/assets/img/flutter/Theory/scrollable_widget/renderCount.gif){: width="50%" }
</center>

#### AxisSpacing
- crossAxisSpacing : 가로로 간격 나눔 (float)
- mainAxisSpacing : 세로로 간격 나눔 (float)

### builder: 화면에 보이는 갯수만큼
#### CrossAxisCount: 지정한 갯수 기준
가로로 지정한 갯수만큼 뷰를 보여줌.
```dart
GridView.builder(
  gridDelegate: SliverGridDelegateWithFixedCrossAxisCount( 
      crossAxisCount: 2 // 가로로 뷰 갯수 고정함
  ),
  itemBuilder:(context, index) {
    return RenderColorContainer(
      color: rainbowColors[index % rainbowColors.length],
      index: index,
    );
  },
);
```

#### CrossAxisEntent: 최대 사이즈 기준
지정한 최대 크기 기준으로 그 최대 크기를 넘지 않는 선에서 가로로 최대로 뷰 갯수를 채움.
```dart
gridDelegate: SliverGridDelegateWithMaxCrossAxisExtent(
  maxCrossAxisExtent: 50, // 최대 크기가 50이 되는 한도 내에서 가로로 꽉 채움.
)
```
<center>
![renderMaxExtent](/docs/assets/img/flutter/Theory/scrollable_widget/renderMaxExtent.gif){: width="50%" }
</center>
