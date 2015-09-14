# WebAPI Basics

How do you turn this on?

# HTML

HyperText Markup Language

描述網頁的結構

```html
<div id="example-id">
  <p class="example-class">
    <button>Text</button>
  </p>
</div>
```

# CSS

Cascading Style Sheet

描述網頁的外觀

```css
#example-id .example-class > button {
  font-size: 16px;
  height: 300px;
  color: red;
}
```

# DOM

Document Object Model

連接 JavaScript 與頁面內容的橋樑

用 JavaScript 操作網頁就靠它了

# Global Object

特殊的全域物件

在瀏覽器裡叫 window

所有其他的全域變數都會自動成為 window 的屬性

# 常用物件

```javascript
// 瀏覽器相關資訊
navigator;
// URL 相關
location;
// 歷史記錄
history;
// 存取網頁介面
document;
```

# 選取元素

CSS selector

```javascript
var btn = document.querySelector('#example-id .example-class > button');
```

# 事件

發生這件事情的時候做那個動作

```javascript
btn.addEventListener('click', function (event) {
  console.info('hello!');
});
```

# 除錯

* Web Console
* debugger statement
* console API

# Web Console

* Inspector: 觀察並修改元素
* Console: 詳細訊息，動態執行程式
* Debugger: 除錯工具

# debugger statement

寫死在 code 裡

沒開 Console 就不會停

# console API

* 印除錯訊息
* 計時

沒看 Console 就看不到

# WebAPI 權限

* non-privileged
  * Hosted or Packaged
* privileged
  * Packaged **and** Signed (i.e. from marketplace)
* certified required
  * (官方特權)

# WebAPI 功能

* Communication
* Hardware Access
* Data Management
* Other

# Communication API

TCPSocket

```javascript
"permissions" : {
  "tcp-socket" : {
    "description" : "Create TCP sockets and communicate over them."
  }
}
```
```javascript
// 連到 localhost:80
var socket = navigator.mozTCPSocket.open('localhost', 80);
// 監聽 localhost:8080 (一定要大於 1024)
var socket = navigator.mozTCPSocket.listen(8080);
```

# TCPSocket

```javascript
// receive
socket.ondata = function onDataReceived () {
  if (typeof event.data === 'string') {
    console.info('Get a string: ' + event.data);
  } else {
    console.info('Get a Uint8Array');
  }
};
// send
function pushData() {
  // Do stuff that retrieves data
  var data = getData();
  // Fill the buffer as much as you can
  while(data != null && socket.send(data));
}
// Resume pushing data when the buffer is flushed
socket.ondrain = pushData;
// Start pushing data
pushData();
```

# Hardware Access API

* Ambient Light Sensor API
* Battery Status API
* Geolocation API
* Pointer Lock API
* Proximity API
* Device Orientation API
* Screen Orientation API
* Vibration API
* WebFM API
* Camera API

# Example: Device Orientation API

```javascript
window.addEventListener("deviceorientation", function (event) {
  var absolute = event.absolute;
  var yaw    = event.alpha;
  var roll     = event.beta;
  var pitch    = event.gamma;
  console.info();
}, true);
```

# Data Management API

* FileHandle API
* IndexedDB API
* Contacts API
* Device Storage API

# Other API

* Alarm API
* Simple Push API
* Web Notifications
* Apps API
* Web Activities
* WebPayment API
* Browser API

# Q&A
