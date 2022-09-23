---
title: "Web View"
template: main.html

---
# Error Fix
## web_view
[Warning: The plugin webview_flutter_android requires Android SDK version 32.](#web_view){: .notice--danger}<br><br>
라는 에러가 발생함. 에러 메시지를 잘 읽어보니 compileSdkVersion을 32로 바꾸라는 것 같아서 그렇게 해줌.<br>
![errorfix1](/assets/img/flutter/webView/webViewErrorFix-1.png)<br>
그리고 webview_flutter READEME에서 minSdkVersion을 19로 바꾸라고 되어 있는데 기본적으로 설정되어 있는 Version을 안 지워주니 error가 발생하는 것이었음.<br>
![errorfix1](/assets/img/flutter/webView/Error-fix3.png)<br>
![errorfix1](/assets/img/flutter/webView/ErrorFix-2.png)<br>
