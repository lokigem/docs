---
title: "Notification"
date: 2022-10-13
template: main.html
---

## SnackBar
```dart
final snackBar = SnackBar(
    content: const Text('Snack bar render successful'),
    action: SnackBarAction(
    label: 'Undo', // Snackbar의 Label에 표시될 이름
    onPressed: () {}, // Label(Undo) 눌렀을 때 실행될 함수
    ), //(1)
);
```

1. ![snackbarRender](/docs/assets/img/flutter/Theory/snackbar/snackBarRender.gif)

### ScaffoldMessenger
```dart
ScaffoldMessenger.of(context).showSnackBar(
    SnackBar(content: Text('인터넷 연결이 원활하지 않습니다.'))
);
```

## showDialog
```dart
showDialog(context: context, builder: (context) { // (1)
    return AlertDialog(
        title: Text("Warning"),
        content: Text("At least one wallet is required"),
        actions: [
        IconButton(onPressed: (){Navigator.of(context).pop();}, icon: Icon(Icons.close)),
        ],
    );
});
```

1. ![show_dilog](/docs/assets/img/flutter/Theory/show_dialog/show_dialog.gif)