---
title: "Text Form Field"
date: 2022-10-22
template: main.html
---

## Introduce
Text Form Field를 활용하면 다수의 Text Field가 있어도 데이터를 동시에 쉽게 입력 받고 에러 처리를 쉽게 해줄 수 있음.

## How To Use
### Global Key 선언
다음과 같은 GlobalKey를 선언해주고 
```dart
class _SettingBottomSheetState extends State<SettingBottomSheet> {
  final GlobalKey<FormState> formKey = GlobalKey();
```
Text Form Field의 부모 위젯을 Form()으로 감싸준 후 key 아까 선언한 formKey를 넣어줌.
```dart
body: Form(
  key: formKey,
  child: TabBarView(
```

### validator: 오류 처리
아래와 같이 코드를 작성하면 Text Form Field에 입력된 값이 null인지, null이 아니라도 입력된 값이 있는지 확인할 수 있음. <br>
조건문의 순서가 중요한데 null인지 먼저 체크를 하지 않고 .isEmpty를 넣으면 오류가 남, 그 이유는 || 조건을 연산할 때 첫 조건이 false면 이후 조건을 진행을 하지 않기 때문. 즉, .isEmpty는 값이 있다는 전제하에 값이 비어있는지 확인하는 것임.
```dart
TextFormField(
validator: (String? val) {
  // null인지 check
  if (val == null || val.isEmpty) {
    return tr('Input Value');
  }

  return null;
},
```

### onSaved
onSaved는 formKey.current!.save()를 실행했을 때 실행되는 함수임.<br>
예시 👇
```dart
onSaved: (val) {
  setState(() {
    periodStartTime = DateTime(
      DateTime.parse(val!).year,
      DateTime.parse(val!).month,
      DateTime.parse(val!).day,
    );
  });
},
```

### onSavePressed() 
보통 저장 버튼을 통해서 validator와 onSaved에 작성한 함수를 활용해주고 있음.
```dart
void onSavePressed() async {
  if(formKey.currentState == null) {
    return null;
  }

  // 오류가 없다면 실행하는 부분
  if(formKey.currentState!.validate()) {
    formKey.currentState!.save();
    Navigator.of(context).pop();
  }
}
```
