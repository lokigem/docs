---
title: "Animated Opacity: 화면 전환"
date: 2022-10-13
template: main.html
---
```dart
AnimatedOpacity( // 동작 화면 : (1)
    opacity: _visible ? 1.0 : 0.0,
    duration: const Duration(milliseconds: 500),
    child: Container(
        width: 200.0,
        height: 200.0,
        color: Colors.green,
    ),
);
```

1. <center>
![animatedOpacity](/docs/assets/img/flutter/Theory/animated_opacity/animatedOpacity.gif)
</center>