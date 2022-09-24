---
title: "Row and Column"
template: main.html
---
## Row and Column 
- row : 세로
- column : 가로 
children을 사용해서 다수의 자식 요소를 넣어줄 수 있음.
### mainAxisAlignment 
주축 정렬, 주축이 column이라면 가로 방향으로, row 라면 세로 방향으로 정렬해줌.
```dart
Column(
  /* MainAxisAlignment - 주축 정렬.
  start - 시작에 정렬.
  end - 끝에 정렬.
  center - 가운데 정렬.
  spaceBetween - 시작과 끝에 배치되고 위젯과 위젯의 사이가 동일하기 배치됨.
  spaceEvenly - 위젯을 같은 간격으로 배치하지만 끝과 끝에도 위젯이 아닌 빈 간격으로 시작함.            spaceArround - spaceEvenly에서 끝과 끝의 간격을 반만 줌.
   */
  mainAxisAlignment: MainAxisAlignment.spaceEvenly,
)
```
### crossAxisAlignment
반대축 정렬, 주축이 column이라면 세로축을 정렬하고 row라면 가로축을 정렬해줌.
```dart
Column(
	// CrossAxisAlignment - 반대축 정렬, 기본값은 center
    // strech - 사이즈 최대 사이즈로 늘림.
	crossAxisAlignment: CrossAxisAlignment.start,
)
```
### mainAxisSize
주축크기 설정.
```dart
Column(
    // 주축 크기, max - 최대, min - 최소
    mainAxisSize: MainAxisSize.min,
)
```
### Expanded or Flexible
Column이나 Row안에만 사용할 수 있음.
#### Flexible
공간을 차지하고 남은 부분을 Column에 돌려줌.
```dart
Column(
	children: [
		// Expanded / Flexible - column이나 row안에다가만 사용할 수 있음.
        Flexible( // 밑에 지정되어 있는만큼의 공간을 차지하고 남은 부분을 Column에 돌려줌.
        child: Container(
			color: Colors.red,
            width: 50.0,
            height: 50.0,
			),
        ),
	]
)
```
#### Exmpanded
공간을 전부 차지하라는 뜻.
```dart
Column(
	children: [
		Expanded( // 남아있는 공간을 모두 차지하라는 뜻.
            child: Container(
            color: Colors.green,
            width: 50.0,
            height: 50.0,
			),
		),	
	]
)
```
## Reference 
[Commit 이력](https://github.com/rookedsysc/Flutter-Study/commits/main/flutterProject/row_and_column)




