---
title: "Hive"
date: 2022-10-18
template: main.html
---

## Hive란?
NoSQL을 사용할 수 있게 해주는 Flutter 패키지 

## How To Install(dependencies)
[hive](https://pub.dev/packages/hive)<br>
[hive-flutter](https://pub.dev/packages/hive_flutter)<br>
[hive-generator](https://pub.dev/packages/hive_generator) - dev_dependencies에 등록

## Custom Object 생성
Custom Object를 생성해줄 때마다 Hive Type을 설정해줘야 하며, 이는 곂치면 **절대로** 안됨.<br>
또 다른 Custom Object를 생성할 경우 Hive Type이 변경됨. Hive Type 마다 Hive Field는 0번부터 시작하며 각각의 Hive Type에서 Field는 곂치면 안됨.
```dart
part 'transaction_record.g.dart';
@HiveType(typeId: 0)
class  Users{
  @HiveField(0)
  String id;
  @HiveField(1)
  String userName;
  @HiveField(2)
  int age;
  
  Users({
    required this.id,
    required this.userName,
    required this.age,
  });
}
```

작성 완료 했으면 

```console
flutter pub run build_runner build
```

명령으로 Code Generation 실행.

### 사용방법
```dart
void main() async {
    WidgetsFlutterBinding.ensureInitialized();
    await Hive.initFlutter();
    Hive.registerAdapter<Users>(UsersAdapter()); 
    final person = await Hive.openBox<Users>('users'); // Custom Object 
}
```