# input 입력받은 값을 화면에 출력하는 방법

input form에 이벤트가 발생했을 때
Javascript로 웹페이지의 DOM에 접근하여,
입력된 값을 가져와서, 웹페이지에 뿌려주는 방법.

## 사용자가 타이핑 할때마다 input 값 출력하기

```html
<input type="text" id="name" />
<div id="result"></div>
```

`<input type="text" id="name" />`  
사용자로부터 값을 입력받을, id='name'인 input element를 생성.
keyup 이벤트(키를 눌렀다가 떼었을 때 발생하는 이벤트)가 발생하면, printName() 메소드를 호출.

`<div id='result'></div>`  
input 폼에 입력받은 값을 출력할 위치.

```javascript
const $input = document.getElementById("name");
const $result = document.getElementById("result");

function printName() {
  const name = $input.value;
  $result.innerText = name;
}

$input.addEventListener("keyup", printName);
```

`const name = $input.value;`  
input element의 value 값을 읽어와서 name에 저장.

`$result.innerText = name;`  
innerText 프로퍼티를 사용해서 text 값을 name으로 변경.

```html
<input type="text" id="name" onkeyup="printName()" />
```

addEventListner는 익스플로러 8 이전 버전에서는 작동하지 않음.
'onkeyup' 이벤트(키보드가 눌려졌을 때 발생하는 이벤트) 사용 가능.

## 사용자가 입력을 완료하면 input 값 출력하기

```javascript
const $input = document.getElementById("name");
const $result = document.getElementById("result");

function printName() {
  const name = $input.value;
  $result.innerText = name;
}

$input.addEventListener("change", printName);
```

사용자가 입력을 완료하고, 마우스 커서를 input form 밖으로 이동시켰을 때
값을 읽어와서 화면에 출력.

```html
<input type="text" id="name" onchange="printName()" />
<div id="result"></div>
```

addEventListner는 익스플로러 8 이전 버전에서는 작동하지 않음.
'onchange' 이벤트 사용 가능
