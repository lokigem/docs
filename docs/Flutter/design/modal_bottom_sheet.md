---
title: "Modal Bottom Sheet"
date: 2022-10-26
template: main.html
---

## Floating Modal Page
[pub.dev 페이지](https://pub.dev/packages/modal_bottom_sheet)<br>

```dart
IconButton( // (1)
    onPressed: () {
    showFloatingModalBottomSheet(
        context: context,
        builder: (context) {
            return ModalFit();
        });
    },
    icon: Icon(Icons.category))),
```

1. ![floatingModalBottomSheet](/docs/assets/img/flutter/design/modal_bottom_sheet/floating_modal_bottom_sheet.gif)

### FloatingModal class
```dart
class FloatingModal extends StatelessWidget {
  final Widget child;
  final Color? backgroundColor;

  const FloatingModal({Key? key, required this.child, this.backgroundColor})
      : super(key: key);

  @override
  Widget build(BuildContext context) {
    return SafeArea(
      child: Padding(
        padding: EdgeInsets.symmetric(horizontal: 20),
        child: Material(
          color: backgroundColor,
          clipBehavior: Clip.antiAlias,
          borderRadius: BorderRadius.circular(12),
          child: child,
        ),
      ),
    );
  }
};
```
### showFloatingModalBottomSheet 함수
```dart
Future<T> showFloatingModalBottomSheet<T>({
  required BuildContext context,
  required WidgetBuilder builder,
  Color? backgroundColor,
}) async {
  final result = await showCustomModalBottomSheet(
      context: context,
      builder: builder,
      containerWidget: (_, animation, child) => FloatingModal(
            child: child,
          ),
      expand: false);

  return result;
}
```


### CategoryModalFit(리스트)
FloatingModalBottomSheet에 보여지는 List Tile
```dart
class ModalFit extends StatelessWidget {
  ModalFit({Key? key}) : super(key: key);
  List<String> items = ['Item1', 'item2', 'Item3', 'Item4'];

  @override
  Widget build(BuildContext context) {
    return Material(
        child: SafeArea(
      child: Column(
        mainAxisSize: MainAxisSize.min,
        children: <Widget>[
          ...List.generate(items.length, (index) {
            return ListTile(
              title: Text(items[index]),
              leading: Icon(Icons.insert_emoticon),
              onTap: () => Navigator.of(context).pop(),
            );
          }),
        ],
      ),
    ));
  }
}
```