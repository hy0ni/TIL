# class 추가/변경/삭제/읽기 (className, classList)

- [class 추가/변경/삭제/읽기 (className, classList)](#class-추가변경삭제읽기-classname-classlist)
  - [class 이름 읽기](#class-이름-읽기)
    - [className](#classname)
    - [classList](#classlist)
  - [class 추가/수정](#class-추가수정)
    - [className](#classname-1)
    - [classList](#classlist-1)
  - [class 삭제](#class-삭제)
  - [class toggle](#class-toggle)
  - [특정 클래스 이름이 class 속성에 포함되는지 확인하기](#특정-클래스-이름이-class-속성에-포함되는지-확인하기)

## class 이름 읽기

### className

className 특정 엘리먼트의 클래스 속성의 값을 가져오거나 설정할 수 있다.

```html
<div id="item" class="foo bar"></div>
```

```javascript
let $elm = document.getElementById("item");

console.log($$elm.className); // foo bar
```

### classList

```html
<div id="item" class="foo bar"></div>
```

```javascript
let $elm = document.getElementById("item");

console.log($elm.classList); // foo bar
console.log($elm.classList.length); // 2
$elm.classList.forEach((item) => console.log(item));
// foo
// bar
```

`$elm.classList`<br>
ement.className과 마찬가지로 classList 속성을 사용해서도 class의 이름을 읽을 수 있다.

`$elm.classList.length`<br>
element의 class에는 여러 개의 class item이 지정될 수 있다.
class item의 개수를 확인하려면 classList.length 속성을 이용한다.

`$elm.classList.forEach(item => console.log(item))`<br>
forEach 반복문을 사용해 class item의 이름을 하나씩 읽어 옴.

## class 추가/수정

### className

```javascript
let $elm = document.getElementById("item");
$elm.className = "baz";

console.log($elm.className); // baz
```

`element.className = '이름'`<br>
기존의 클래스 이름을 모두 삭제하고 새로 설정할 때는
element.className 속성에 직접 값을 지정해 주면 된다.

```javascript
let $elm = document.getElementById("item");
$elm.className += " baz";

console.log($elm.className); // baz
```

`element.className += ' 이름'`<br>
기존의 클래스에 값을 추가하려면, 기존의 className에 추가하려는 값을 문자열로 연결해 주면 된다.<br>
이때 스페이스도 같이 추가해 줘야 한다.

### classList

```javascript
let $elm = document.getElementById("item");
$elm.classList.add("baz");

console.log($elm.className); // foo bar baz
```

classList'는 readonly 속성이기 때문에, 직접 값을 지정할 수 없으므로,

`element.classList.add('이름')`<br>
element.classList.add() 메서드를 사용해서 class를 추가할 수 있다.<br>
element.classList.add() 메서드는 문자열 앞에 스페이스를 입력하지 않아도 된다.<br>
추가하려는 클래스가 이미 class 속성에 포함되어 있다면 추가되지 않는다.

```javascript
let $elm = document.getElementById("item");
$elm.classList.add("baz", "bazz");

console.log($elm.className); // foo bar baz bazz
```

`element.classList.add('이름1', '이름2'...)`<br>
element.classList.add() 함수에 파라미터를 여러 개 전달하여
한 번에 여러 개의 클래스를 추가할 수도 있다.

```javascript
let $elm = document.getElementById("item");
$elm.classList.replace("foo", "baz");

console.log($elm.className); // baz bar
```

`element.classList.replace('변경 전 이름', '변경 후 이름')`<br>
기존의 class 속성에서 특정 class item을 찾아서, 해당 item의 이름을 변경할 수 있다.

## class 삭제

```javascript
let $elm = document.getElementById("item");
$elm.classList.remove("foo");

console.log($elm.className); // bar
```

`element.classList.remove('삭제할 클래스명1', '삭제할 클래스명2'...)`<br>
element.classList.remove() 메서드 이용해서 원하는 class item을 삭제할 수 있다.

## class toggle

```html
<button id="btn" type="button">toggle button</button>
```

```javascript
let $btn = document.getElementById("btn");

function toggleClass() {
  $btn.classList.toggle("foo");
  console.log($btn.classList);
}

$btn.addEventListener("click", toggleClass);
```

`element.classList.toggle('toggle 할 클래스 이름')`<br>
element.classList.toggle()은 만약 element의 클래스 목록에 해당 클래스가 있으면 제거하고,
클래스가 없으면 추가한다.

## 특정 클래스 이름이 class 속성에 포함되는지 확인하기

```javascript
let $elm = document.getElementById("item");

console.log($elm.classList.contains("foo")); // true
console.log($elm.classList.contains("baz")); // false
```

`element.classList.constains()`<br>
특정 클래스 이름이 element의 class 속성에 포함되어 있는지 확인한다.
해당 속성이 포함되어 있으면 true를 리턴하고, 포함되어 있지 않으면 false를 리턴한다.
