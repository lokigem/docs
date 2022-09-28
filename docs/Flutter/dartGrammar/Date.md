---
title: "Dart Date"
date: 2022-09-25
template: main.html
---


[기본 자료형](https://github.com/rookedsysc/Flutter-Study/blob/dartGrammar/Grammar/DataType.dart)

## Final과 Const

[Final과 Const](https://github.com/rookedsysc/Flutter-Study/blob/dartGrammar/Grammar/final_and_const.dart)
## Operation:: is와 is!
[Operation:: is와 is!](https://github.com/rookedsysc/Flutter-Study/commit/27eec1b2fad060393648e8f7ed6a8ada2e6a1440)
## List와 Map
[List와 Map](https://github.com/rookedsysc/Flutter-Study/commit/2046748443b5237be5c310587b533becee62de2c)
## Set
[Set](https://github.com/rookedsysc/Flutter-Study/commit/710622428dd3ecd1fd8183e4b96df4116eb975fd)
## 조건문
[조건문](https://github.com/rookedsysc/Flutter-Study/commit/0c056730dd07ba90079adc20cd66f911d8855d58)
## 반복문
[반복문](https://github.com/rookedsysc/Flutter-Study/commit/b7e1c0a26e2fdb5d1e1b66c0ea627b6e20ba42be)
## enum
[enum](https://github.com/rookedsysc/Flutter-Study/commits/dartGrammar/Grammar)
## 함수와 typedef
signature: return 타입과 parameter의 형태를 signature라고 함 <br>
typedef로 선언해놓은 함수에 같은 시그니처의 함수를 대입해주고 해당 typedef를 이용해서 연산을 수행해줌.
```dart 
// typedef 선언
typedef Operation = int Function(int x, int y, int z);
// 같은 시그니처의 method 선언.
int substact (int x, int y, int z) => x - y - z;
// 사용, 같은 시그니처의 함수를 대입해서 연산해줌.
operation = substact;
int result2 = operation(30, 20, 5);
```

## DateTime
### 현재 시간 구하기
```dart
DateTime now = DateTime.now();
```
### DateTime Type별 출력
```dart 
print(now.year);
print(now.month);
print(now.day);
print(now.hour);
print(now.second);
print(now.minute);
print(now.microsecond);
```
## 시간 지정하기
```dart
DateTime SpecifyDay = DateTime(
	int year,
	int month,
	int day,
	int time,
	int minutes,
	int seconds,
);
```

## 간격 구하기 
```dart
targetTime.differenc(comparisonTime); // tagetTime - comparisonTime
```

## 시간 사칙연산
```dart
targetTime.add(Duration(hours: 10); // 시간 덧셈
targetTime.subtract(Duration(minutes: 5)); // 분 뺄셈
```

## Reference
[Dart Date](https://github.com/rookedsysc/Flutter-Study/blob/dartGrammar/Grammar/functionalProgramming/dartDate.dart)
