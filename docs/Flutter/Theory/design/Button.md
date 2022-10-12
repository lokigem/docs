---
title: "Button"
date: 2022-09-27
template: main.html
---
## Button의 종류 
- ElevatedButton : 약간 3D 형로 돌출되어 있고 배경 있음.
- OutlinedButton : 테두리와 텍스트만 있음.
- TextButton : 텍스트만 있음.

### styleFrom을 통해서 속성 넣기
Button의 Structor, style에 ButtonType.styleFrom()을 넣어주고 여기에 Style을 지정해줄 수 있음.<br> styleForm은 ButtonStyle() class를 상속받고 있음.

> 예시

```dart
OutlinedButton(onPressed: (){}, child: Text('OutlinedButton'),
	style: OutlinedButton.styleFrom(
        // 글자와 애니메이션 효과의 색상을 변경해줌.
        // 배경 색상은 backgroundColor에 넣어서 사용가능하긴 함, 근데 그러면 OutlinedButton을 사용하는 이유가 없음.
        primary: Colors.green,
		textStyle: TextStyle(
                fontWeight: FontWeight.w700, // 텍스트 굵기 
                fontSize: 20.0, // 텍스트 사이즈 
		),
    ),
),
```

### resolveWith를 사용해서 Button의 속성을 지정해주는 방법

#### material state
Material State는 Flutter 전반적으로 (앱, 웹, 데스크탑 앱 전체 포함) 사용하게 되는 기본적인 상태들임.<br>
- hovered : 호버링 상태 (마우스 커서를 올려놓은 상태) - 모바일 사용 불가<br>
- focused : 포커스 됐을 때 (텍스트 필드)<br>
- pressed : 눌렀을 때<br>
- dragged : 드래그 됐을 때 (o)<br>
- selected : 선택됐을 때 (체크박스, 라디오 버튼)<br>
- scrollUnder : 다른 컴포넌트 밑으로 스크롤링 됐을 때<br>
- diabled : 비활성화 됐을 때 (Button에서 onPressed: null 해버리면 비활성화 상태가 됨.) (o)<br>
- error : 에러상태 (텍스트 필드에서 많이 사용함.)<br>

#### resolveWith
- MaterialSatePropert

> Material State의 집합으로 정의되는 위젯의 대화형 "상태"를 기반으로 유형 값으로 확인 되는 [class](https://lokigem.github.io/docs/Flutter/dartGrammar/oopProgramming/#class)용 [인터페이스](https://lokigem.github.io/docs/Flutter/dartGrammar/oopProgramming/#interface-abstract)임. <br>

- resolveWith 

> resolveWith에는 함수를 넣어줘야 하며 **반드시 return값을(null이라도) 받아야함.** Set <MeterialState\> states에는 현재 위젯(Button)의 Meterail State 값이 들어가게 됨.

##### 사용 예시
```dart
foregroundColor: MaterialStateProperty.resolveWith((Set<MaterialState> states) {
	// states에 MaterialState.pressed 상태값을 포함 중이라면 if 문 진입
	if(states.contains(MaterialState.pressed)){
	  return Colors.white;
	}
	// resolveWith를 사용하게되면 함수를 넣어줘야 하므로 반드시 return 값을(null 이라도) 가져야 함.
	return Colors.red;
}
```
##### 참조 
[Button Project](https://github.com/rookedsysc/Flutter-Study/blob/main/Theory/flutter-lv1-theory-statefulwidget-before-main/lib/screen/home_screen.dart)


