# input 박스에 숫자만 입력되도록 설정하기 (4가지 방법)

- [input 박스에 숫자만 입력되도록 설정하기 (4가지 방법)](#input-박스에-숫자만-입력되도록-설정하기-4가지-방법)
  - ['type'을 'number'로 지정하기](#type을-number로-지정하기)
    - [min, max, step 속성 지정하기](#min-max-step-속성-지정하기)
  - [입력된 key 체크하기](#입력된-key-체크하기)
  - [oninput 이벤트, 정규식, replace() 함수 활용하기](#oninput-이벤트-정규식-replace-함수-활용하기)
  - [pattern 속성 활용하기](#pattern-속성-활용하기)

## 'type'을 'number'로 지정하기

```html
<input type='number'></input>
```

input의 type 속성을 'number'로 지정하면, 숫자만 입력받을 수 있음.<br>
브라우저에 따라서, 입력창 오른쪽에 숫자 증감 아이콘도 생성된다.

### min, max, step 속성 지정하기

```html
<form>
  <input type="number" min="10" max="30" step="3" />
  <input type="submit" />
</form>
```

input의 type을 'number'로 지정한 경우,<br>
min, max 속성을 추가하여 최대값과 최소값을 지정할 수 있다.<br>
step 속성은, 입력받을 숫자들의 간격이다.

위, 예제는 10, 15, 20, 25, 30 만 입력받을 수 있다.<br>
이 이외의 숫자들이 입력 된 경우, 제출(submit) 버튼을 클릭하면, 오류 메세지가 나온다.

## 입력된 key 체크하기

```html
<input type="text" onkeypress="return checkNumber(event)" />
```

<input type='text' onkeypress='return checkNumber(event)'>

input type 'text'로 지정.
onkeypress 이벤트가 발생하면 checkNumber 함수를 호출하여 결과를 리턴함.

```javascript
function checkNumber(event) {
  if (
    event.key === "." ||
    event.key === "-" ||
    (event.key >= 0 && event.key <= 9)
  ) {
    return true;
  }

  return false;
}
```

checkNumber() 함수는 keyboard event를 입력받아,<br>
입력된 값이 숫자인 경우 true를 리턴하여 input에 입력되게 하고,<br>
그렇지 않은 경우에는 false를 리턴하여 input에 입력되지 않도록 함.

마우스로 숫자가 아닌 값을 붙여넣기 하면 입력이 된다는 단점이 있다.

## oninput 이벤트, 정규식, replace() 함수 활용하기

```html
<input
  type="text"
  oninput="this.value = this.value.replace(/[^0-9.]/g, '').replace(/(\..*)\./g, '$1');"
/>
```

'oninput' 이벤트는 input form의 값이 바뀌면 발생한다.<br>
oninput 이벤트가 발생했을 때, 숫자만 입력할 수 있는 정규식을 적용하여,<br>
숫자가 아닌 다른 값이 입력되면 replace() 함수를 사용해 값이 대체되도록 함.

## pattern 속성 활용하기

```html
<form>
  <input type="text" pattern="[0-9]+" />
  <input type="submit" />
</form>
```

```css
input:invalid {
  border: 4px solid red;
}
```

input에 pattern 속성을 지정하고, 입력한 값을 검증할 정규식을 입력.<br>
위 pattern 속성에 지정된 정규식은 숫자만 입력받도록 작성.<br>
만약, 숫자가 아닌 다른 문자가 입력된다면, '제출(submit)' 버튼 클릭 시 메시지를 표시한다.

css에 input:invalid 속성을 지정하면
input에 입력된 값이 pattern에 맞지 않을 경우(즉, 숫자가 아닌 다른 값이 입력되면)
즉시, input:invalid에 적용된 CSS를 적용해 input 필드의 색을 변경한다.
