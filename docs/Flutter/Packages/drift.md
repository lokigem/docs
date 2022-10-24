---
title: "Drift"
date: 2022-10-18
template: main.html
---

## 테이블 구조 정의

다음과 같은 컬럼을 만들어주기 위해서는 

|ID|Category|DataTime|
|--|--------|--------|
|데이터|데이터|데이터|
|데이터|데이터|데이터|
|데이터|데이터|데이터|

```dart
import 'package:drift/drift.dart';

class Schedules extends Table {
  // 함수를 return 해주기 때문에 ()를 한 번 더 붙여줘야 함.
  IntColum get id => integer()();
  TextColumn get category => text()();
  DateTimeColumn get dataTime => dateTime()();
}
```

와 같이 생성해줘야 함.

### 테이블 Column 종류
- IntColumn
- DataTimeColumn
- TextColumn

## 테이블 생성

```dart
import 'package:drift/drift.dart';
import 'package:path/path.dart' as p;
import 'package:path_provider/path_provider.dart';
import 'package:drift/native.dart';

// private 값도 불러올 수 있게 해줌
// 파일 생성 당시에는 없지만 Code Generation을 해주면 생성될 파일
// 파일 이름은 '현재 파일의 이름.g.dart'로 정해줌
part 'drift_database.g.dart';

@DriftDatabase(
  tables: [
    // 괄호 없이 type 선언하듯이 넣어줘야 함
    ClassName, // 위에서 구성한 테이블
    ...
  ]
)

// _$LocalDatabase 파일은 drift_database.g.dart 파일에 생성될 거임
class LocalDatabase extends _$LocalDatabase {
  LocalDatabase() : super(_openConnection());

}

// 하드 드라이브의 어떤 위치에다가 DB를 저장할건지 명시해줌
LazyDatabase _openConnection() {
  return LazyDatabase(() async{
    // os에서 app별로 사용할 수 있는 위치를 지정해주는데 이를 가져오는 것임
    final dbFolder = await getApplicationDocumentsDirectory();
    // 무조건 dart io import
    // join은 경로를 붙여주는 거임 (위에서 구한 경로 + 내가 정한 파일 이름)
    final file = File(p.join(dbFolder.path, "db 이름")); 
    return NativeDatabase(file);
  });
}
```

### Code Generation 실행
작성 이후 Code Generation으로 Code를 생성해줘야 함.

```python
flutter pub run build_runner build # (1)
```

1. ![before](/docs/assets/img/flutter/packages/drift/code_generation_before.png)<br>
<br> <center>실행 후👇 <br><br>
![after](/docs/assets/img/flutter/packages/drift/code_generation_after.png)
</center>

### schemaVersion 오버라이드 하기
code generationd으로 코드를 생성해준 후 원래있던 코드의 LocalDatabase의 Class에서 schemaVersion을 override 해줘야 함. 이는 Database의 구조가 바뀔 때마다 변경해줘야 됨.
```dart
class LocalDatabase extends _$LocalDatabase {
  LocalDatabase() : super(_openConnection());

  @override
  int get schemaVersion => 1;
}
```

### DataBase 불러오기
불러오는 곳의 함수를 async 함수로 변환해주고 불러와야 함. 
```dart
import 'package:패키지명/database선언 경로/데이터 베이스 이름.dart';
// ex)
// import 'package:scheduler_lab/database/drift_database.dart';

void main() async {
  final database = LocalDatabase();
```


## Data 가져오기 

### get 함수 선언
만약에 내가 선언해서 가져오고 싶은 데이터 베이스의 이름이 Content라면 select() 안에는 select가 들어가고 Generic은 ContentData에서 가져오게 됨.
```dart
class LocalDatabase extends _$LocalDatabase {
  LocalDatabase() : super(_openConnection());

  Future<List<ContentData>> getAllContentsEntries() =>
      // ex) Budget이 클래스 명이면 (budget)
      select(content).get(); 
```

### 데이터 가져오기
```dart
final database = LocalDatabase();
// List<Content> 형식으로 저장됨
final contents = await database.getAllContentsEntries(); 
```

## Data 삽입(insert)
값을 삽입할 때는 내가 정의했던 Class명에다가 Companion을 붙인 클래스에 값을 넣어줘야 함.
```dart
class LocalDatabase extends _$LocalDatabase {
  LocalDatabase() : super(_openConnection());

  Future<int> createContent(ContentCompanion data) =>
      into(content).insert(data);
```

### 함수 사용하기
값을 넣어줄 때 값은 Value()에 감싸서 넣어줘야 함.
```dart
database.createContent(ContentCompanion(
  인자1 : Value(값),
  인자1 : Value(값),
));
```

