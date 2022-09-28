---
title: "Functional Programming"
date: 2022-09-23
template: main.html
---
## map 
```dart 
.map((x) => return);
.map((x){
	code
};
```
[map 참조](https://github.com/rookedsysc/Flutter-Study/blob/main/Grammar/functionalProgramming/map.dart)
## reduce 
reduce 사용시 parameter의 data tyep과 return result의 data type이 같아야 함.<br>
배열의 끝까지 loop 발생, 첫 번째는 prev + next 해주고 그 이후로는 total + next 해줌.
```dart
.reduce((prev, next) => code);
```
### fold 
reduce와는 다르게 return tyep과 parameter type이 같지 않아도 됨.<br>
대신, 선언해줄 때 return type을 설정해줘야 하며 (prev, next)전에 첫 번째 parameter를 받고 이를 첫 번째 계산값으로 사용함.<br>
```dart
.fold<returnType>(0, (prev, next) => prev + next);
```
[reduce and fold 참조](https://github.com/rookedsysc/Flutter-Study/blob/main/Grammar/functionalProgramming/reduce.dart)
## where
where((x) => 조건); 조건이 true인 값만 return 해줌.<br>
```dart
where((x) => 조건); 
```
[where 참조](https://github.com/rookedsysc/Flutter-Study/blob/main/Grammar/functionalProgramming/where.dart)
## cascading operator 
List 이어주는 기능(?)<br>
[cascading operator](https://github.com/rookedsysc/Flutter-Study/blob/main/Grammar/functionalProgramming/cascading_oprator.dart)
## functional programming 사용 예시
<details>
<summary>예시1</summary>
<div markdown="1">
```dart
void main() {
  String number = '12345';
  final numberJPEG = number.split('').map((x) => '$x.jpeg').toList();
  print(numberJPEG);
  example2();
  example3();
}

// Map > Map use map
void example2() {
  Map<String, String> harryPoter = {
    "Harry Potter" : "해리 포터",
    "Ron Weasley" : "론 위즐리",
    "Hermione Granger" : "헤르미온느 그레인저"
  };

  // map > map // Map Entry는 class 임. MapEntry(key, value)순으로 되어 있으며 key와 value에 각각 접근해서 return 해줌.
  final result = harryPoter.map((key, value) => MapEntry(
    'Harry Poter Character $key',
    '해리포터 캐릭터 $value',
    ),
  );
  print(result);

  final keys = harryPoter.keys.map((x) => 'HPC $x').toList;
  print(keys);
}

void example3() {
  Set blackPinkSet = {
    '로제', '지수', '제니', '리사',
  };

  final newSet = blackPinkSet.map((x) => '블랙핑크 $x');

  print(newSet);
}
```

> 출력값

```console
[1.jpeg, 2.jpeg, 3.jpeg, 4.jpeg, 5.jpeg]
{Harry Poter Character Harry Potter: 해리포터 캐릭터 해리 포터, Harry Poter Character Ron Weasley: 해리포터 캐릭터 론 위즐리, Harry Poter Character Hermione Granger: 해리포터 캐릭터 헤르미온느 그레인저}
[HPC Harry Potter, HPC Ron Weasley, HPC Hermione Granger]
(블랙핑크 로제, 블랙핑크 지수, 블랙핑크 제니, 블랙핑크 리사)
```

</div>
</details>

<details>
<summary>예시2 </summary>
<div markdown="1">
```dart
void main() {
  List<Map<String, String>> people = [
    {
      "name" : "로제",
      "group" : "블랙핑크",
    },
    {
      "name" : "지수",
      "group" : "블랙핑크",
    },
    {
      "name" : "RM",
      "group" : "BTS",
    },
    {
      "name" : "뷔",
      "group" : "BTS",
    },
  ];

  print(people);

  final parsedPeople = people.map((x) => Person(
    name: x['name']!, // 값이 반드시 존재한다는 뜻. ! 안붙여주면 참조 error 발생함.
    group: x['group']!,
  )).toList();

  print(parsedPeople);

  for(Person person in parsedPeople) {
    print(person.name);
    print(person.group);
  };

  final bts = parsedPeople.where(
    (x) => x.group == "BTS",
  );
}

class Person {
  final String name;
  final String group;

  Person({
    required this.name,
    required this.group,
  });

  // class의 초기 값들은 Instance of 라는 형식으로 저장이 됨.
  // print를 했을 때 어떤 형식을 취하는지 object class에 String으로 정의되어 있는데 이를 바꿔줌으로서 출력형태를 바꿔줌.
  @override
  String toString(){
    return 'Person(name: $name, group: $group';
  }

}
```
</div>
</details>
