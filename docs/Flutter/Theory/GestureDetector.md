---
title: "Gesture Detector"
date: 2022-10-05
template: main.html
---
## Gesture Detector 
Widget에서 Gesutre가 감지될 때 실행될 함수를 정의해줄 수 있음.
```dart
GestureDetector(
	onTap() {
		실행할 함수
	}
)
```
### Focus 해제하기 
다음 함수는 Focus를 해제해줌. 즉, 키보드를 입력하다가 onTap() {} 안에 실행할 함수로 넣어주면 키보드의 포커싱이 해제됨.
```dart
FocusScope.of(context).requestFocus(FocusNode());
```
