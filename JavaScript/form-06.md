# Caps Lock 키 활성화 여부 체크하기

입력창에 뭔가가 입력되면,<br>
사용자의 키보드에 Caps Lock 키가 활성화되어 있을 경우,<br>
입력창 아래쪽에 'Caps Lock이 켜져 있습니다'라는 메시지를 보여준다.

```html
<input id="name" onkeyup="checkCapsLock(event)" />
<div id="message"></div>
```

`onkeyup="checkCapsLock(event)"`

입력창에 키보드로 뭔가를 입력하면,<br>
키보드를 눌렀다가 떼는 순간(onkeyup)에<br>
Caps Lock 키가 눌렸는지를 체크하는 checkCapsLock 함수를 호출한다.

```javascript
function checkCapsLock(event) {
  if (event.getModifierState("CapsLock")) {
    document.getElementById("message").innerText = "Caps Lock이 켜져 있습니다.";
  } else {
    document.getElementById("message").innerText = "";
  }
}
```

`event.getModifierState("CapsLock")`<br>
checkCapsLock 함수에서는 전달받은 event의 getModifierState 함수를 호출한다.

## KeyboardEvent.getModifierState() 함수

```javascript
getModifierState(key);
```

이벤트가 발생했을 때 Alt, Shift, Ctrl, 또는 Meta 등의 보조 키가 눌렸는지를 나타내는 boolean 값을 반환한다.<br>
key 값은 대소문자를 구분한다.

대표적으로 아래 key 문자열을 파라미터로 전달하여, 각 key의 상태를 체크할 수 있다.

- CapsLock
- NumLock
- ScrollLock
- Alt
- Shift
- Ctrl
