---
title: "Dart Date"
date: 2022-09-25
template: main.html
---
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

## 포매팅
### 문자열을 DateTime으로
```dart
DateTime.parse( String )
```
#### 예시
```dart
void main() {
  String nowTime = '2021-10-23 14:00:32';
  print(DateTime.parse(nowTime)); // 출력
  print(DateTime.parse(nowTime).runtimeType); // DateTime 출력
}
```
### DateTime을 문자열로 
포맷 형식대로 DateTime을 포맷해서 문자열로 return 해줌. 포맷 형식은 구글링해보면 많이 나옴.
```dart
DateFormat( 포맷 형식 ).format( DateTime something )
```
#### 예시
```dart
import 'package:intl/intl.dart';

void main() {
  DateTime timeOfBirth = DateTime(2021,12,21,14,30);
  DateTime birthDay = DateTime(2021,12,21);
   
  if (birthDay == timeOfBirth) {
    print('birthDay and timeOfBirth is a same day'); // 출력 안됨
  } else {
    print('birthDay and timeOfBirth is not a same day'); // 출력
  }
  
  if (DateFormat('yyyy-MM-dd').format(timeOfBirth) == DateFormat('yyyy-MM-dd').format(birthDay)) {
    print('DateFormat is working'); // 출력
  }
}
```



## Reference
[Dart Date](https://github.com/rookedsysc/Flutter-Study/blob/dartGrammar/Grammar/functionalProgramming/dartDate.dart)
