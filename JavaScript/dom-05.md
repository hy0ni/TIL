# 선택자, DOM 특정 요소(element) 찾기

- [선택자, DOM 특정 요소(element) 찾기](#선택자-dom-특정-요소element-찾기)
  - [getElementById()](#getelementbyid)
  - [getElementsByClassName()](#getelementsbyclassname)
  - [getElementByTagName()](#getelementbytagname)
  - [querySelector()](#queryselector)
  - [querySelectorAll()](#queryselectorall)

```html
<h1 id="title" class="my-class"></h1>
<div class="my-class my-class1"></div>
<p class="my-class1"></p>
```

## getElementById()

```javascript
const $h1 = document.getElementById("title"); // h1#title
```

파라미터로 찾으려는 id를 전달하여, 해당 element를 찾을 수 있다.
id는 유일한 값이므로, 하나의 element만 리턴한다.

## getElementsByClassName()

```javascript
const $divList = document.getElementsByClassName("my-class");

const $divListAll = document.getElementsByClassName("my-class my-class1");
```

getElementsByClassName() 함수는 클래스 이름으로 element를 찾아서, 이 클래스 이름을 가지는 모든 element 목록을 리턴한다.

Element's'가 복수 형태인 것은 이 함수가 목록을 리턴하기 때문이다.

다수의 클래스 이름을 모두 포함하고 있는 element를 찾을 때는 파라미터로 클래스 이름을 스페이스로 구분하여 넘겨준다.

## getElementByTagName()

```javascript
const $h1 = document.getElementsByTagName("h1");
```

getElementByTagName()함수는 주어진 태그 이름을 가진 모든 element 목록을 찾아준다.

다수의 element를 리턴하기 때문에
함수명에 복수형의 Element's'가 포함되어 있다.

## querySelector()

```javascript
const $h1 = document.querySelector("#title");
const $div = document.querySelector(".my-class");
const $divTag = document.querySelector("div");
```

querySelector() 함수는 파라미터로 입력받은 CSS 선택자를 사용해서 element를 찾아준다.

파라미터로 입력받은 CSS 선택자로 찾은 여러 개의 element 중 첫 번째 element를 리턴한다.

`document.querySelector("#title")`<br>
**id로 찾기**: id 이름 앞에 '#'를 붙여서 파라미터로 넘겨준다.

`document.querySelector(".my-class")`<br>
**Class로 찾기**: 클래스 이름 앞에 '.'을 붙여서 파라미터로 넘겨준다.

`document.querySelector("div")`<br>
**Tag로 찾기**: 태그 이름으로 element를 찾을 때는 태그명을 문자열로 넘겨준다.

## querySelectorAll()

```javascript
const $class = document.querySelectorAll(".my-class");
```

CSS선택자(파라미터로 넘겨준)로 찾은 모든 element 목록을 리턴한다.

```javascript
const $class = document.querySelectorAll(".my-class, .my-class1");
```

`document.querySelectorAll(".my-class, .my-class1")`<br>
선택자를 ','로 구분한 문자열을 넘겨주면
각각의 선택자에 해당하는 모든 element를 리턴한다.
