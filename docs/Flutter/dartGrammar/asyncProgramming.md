---
title: "Async Programming"
date: 2022-09-23
template: main.html
---
# Async Programming
기존의 cpu의 동작은 실행한 코드가 있으면 해당 코드가 실행이 될 때까지 다음 동작을 실행할 수 없었음.<br>
이는 http 요청 같은 작업을 할 때 문제가 발생하는데, 서버에서 요청값을 받아오기 전까지 cpu가 수행할 수 있는 동작이 아무것도 없어진다는 문제점이 발생함.<br>
다음은 기존 cpu의 동작 방식 👇<br>
![cpu_work](/docs/assets/img/flutter/DartGrammar/cpu_work.jpg)<br><br>
이를 해결하기 위해서 등장한 방식이 바로 Async Programming인데, **비동기 프로그래밍**이라고도 불리며 현재 실행중인 동작이 완료되지 않더라도 다음 동작을 실행하는 것을 뜻함.<bR>
![asynchronous.jpes](/docs/assets/img/flutter/DartGrammar/asynchronous.jpeg)<br>

## Future and await
Future 데이터 타입으로 정의할 수 있으며, Future 관련 method 등을 써줄 수 있음.<br>
```dart
Future<returnType> functionName(Parameter1, Parameter2...) async {
```
### Future.delayed
첫 파라미터에는 지연할 기간(얼마나 지연할건지) Duration 값을 넣어주고 두 번째 파라미터에는 지연시간이 지난 후 실행할 함수를 넣어줌.
```dart
Future.delayed(Duration(seconds: ), () {}
```
### await 
await을 사용하기 위해선 함수에다가 async를 추가해야지 사용할 수 있음. 
```dart
void main() async {
	await 실행할함수();
}
```
### Future and await 참조
[Future and await 참조 1](https://github.com/rookedsysc/Flutter-Study/blob/main/flutterGrammar/asyncProgramming/future.dart)<br>
[Future and await 참조 2](https://github.com/rookedsysc/Flutter-Study/blob/main/flutterGrammar/asyncProgramming/await.dart)
## Stream
리스너를 생성해서 리스너가 리스닝을 하고 있는 동안 controller가 값을 넣어주면 함수가 실행됨. <br>
이 때 return 되는 값들을 지속적으로 반환해줌.
![Stream](/assets/img/flutter/DartGrammar/Stream.png)
### 예시 
```dart
import 'dart:async';

void main() {
  final controller = StreamController();
  // asBroadcastStream을 이용해줘야 여러번 listening을 할 수 있음.
  final Stream = controller.stream.asBroadcastStream();

  // 짝수만 출력
  // 리스너 생성, 이 리스너가 리스닝을 하고 있을 때 값이 들어오면 함수가 실행됨.
  final streamListener1 = Stream.where((val) => val % 2 == 0).listen((val) {
    print('Listener1 : $val');
  });

  // 홀수만 출력
  final streamListener2 = Stream.where((val) => val % 2 == 1).listen((val) {
    print('Listener2 : $val');
  });

  // controller를 통해서 리스너에 값을 넣어줌
  controller.sink.add(1);
  controller.sink.add(2);
  controller.sink.add(3);
  controller.sink.add(4);
}
```
#### Reference
[참조 1](https://github.com/rookedsysc/Flutter-Study/blob/main/flutterGrammar/asyncProgramming/test.dart)<br>
[참조 2](https://github.com/rookedsysc/Flutter-Study/blob/main/flutterGrammar/asyncProgramming/test3.dart)
