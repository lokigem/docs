---
title: "Basic Grammar"
date: 2022-09-18
template: main.html
---

## 기본자료형

[기본 자료형](https://github.com/rookedsysc/Flutter-Study/blob/dartGrammar/flutterGrammar/flutterDataType.dart)

## Final과 Const
[Final과 Const](https://github.com/rookedsysc/Flutter-Study/blob/db4bc1b31c8eb0f5ca547b7d45ea031e2cf2ba3c/flutterGrammar/final_and_const.dart)

### const re-build
[const로 선언된 property](https://github.com/rookedsysc/Flutter-Study/blob/main/flutterProject/const_structor/lib/screen/home_screen.dart)는 re-build를 해도 다시 load되지 않음.<br>
아래는 hot restart를 통해서 처음 build가 되고 난 이후에 "빌드" button을 눌려도 const로 선언된 label1 property는 다시 load되지 않는 현상 👇.<br>
![rebuildFailed](/docs/assets/img/flutter/DartGrammar/constBuild.gif)
#### Reference
[setState란?](http://lokigem.github.io/docs/Flutter/flutterTheory/widget/#setstate)

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
[enum](https://github.com/rookedsysc/Flutter-Study/commits/dartGrammar/flutterGrammar)
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
[함수와 typedef](https://github.com/rookedsysc/Flutter-Study/commit/2961231678821071d95b016158bc990780ee2b6e)

