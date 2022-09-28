---
title: "Builder"
date: 2022-09-28
template: main.html
---
## Builder 
Flutter에서 모든 위젯은 builder() 함수를 가지고 인자값으로 context를 전달함. 

### context
Widget tree에서 현재 Widget의 위치를 알 수 있는 정보.

### builder: (_)의 의미
> builder 함수들은 위젯의 build 함수와 같이 첫번째 파라미터에 BuildContext가 제공됩니다. 그래서 (BuildContext context){} 이 표현을 (\_){} 이렇게 한것뿐입니다.<br>
> 특정 파라미터를 \_로 표현하는 경우 일반적으로 개발자들이 사용하지 않을 파라미터라는 뜻을 전달하기위한 목적이 있습니다.<br>

[참조](https://www.inflearn.com/questions/535754)

