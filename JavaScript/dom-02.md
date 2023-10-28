# innerText와 innerHTML의 차이점

```javascript
let $elm = document.querySelector(".content");

console.log($elm.innerText); // A
console.log($elm.innerHTML); // A
```

`element.innerText`<br>
이 속성은 element 안의 text 값들만을 가져온다.

`element.innerHTML`<br>
innerText와는 달리 innerHTML은 element 안의 HTML이나 XML을 가져온다.

## 값 설정하기 (innerText vs innerHTML)

```javascript
let $elm = document.querySelector(".content");
$elm.innerText = "<p>A</p>";
```

```html
<p>A</p>
```

` $elm.innerText = "<p>A</p>"`<br>
element.innerText에 html을 포함한 문자열을 입력하면,
html코드가 문자열 그대로 element안에 포함된다.

```javascript
let $elm = document.querySelector(".content");
$elm.innerHTML = "<p>A</p>";
```

```html
A
```

`$elm.innerHTML = "<p>A</p>"`<br>
element.innerHTML 속성에 html코드를 입력하면,
html element가 element안에 포함된다.
