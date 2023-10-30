# input에서 입력 글자 수 제한하기

- [input에서 입력 글자 수 제한하기](#input에서-입력-글자-수-제한하기)
  - [maxlength 속성 사용하기](#maxlength-속성-사용하기)
  - [input type이 'number'인 경우 입력된 글자 수 체크로직 구현하기](#input-type이-number인-경우-입력된-글자-수-체크로직-구현하기)

## maxlength 속성 사용하기

```html
<input type="text" maxlength="5" />
```

maxlength 속성을 지정하여 최대 입력 글자수를 제한할 수 있다.

`maxlength='5'`  
최대 5글자까지만 입력이 가능.

이 방법은  
input의 type이 'text, search, url, tel, email, password' 일 경우에만 유효함.  
type이 'number'일 경우에는 유효하지 않음.

## input type이 'number'인 경우 입력된 글자 수 체크로직 구현하기

```html
<input type="number" oninput="handleOnInput(this, 5)" />
```

첫 번째 파라미터로 이벤트가 일어난 element(input element) 전달.  
두 번째 파라미터로 최대 입력 글자 길이(5) 전달.

```javascript
function handleOnInput(el, maxlength) {
  if (el.value.length > maxlength) {
    el.value = el.value.substring(0, maxlength);
  }
}
```

입력창에 oninput 이벤트가 발생할 때마다 호출되는 이 함수는
입력창에 입력된 숫자의 길이가 두번째 파라미터로 입력받은 maxlength보다 크면
입력된 값을 5자리까지 잘라서 입력창의 value값으로 넣어준다.

문자열을 5자리까지 잘라주기 위해 substring 함수를 사용함.  
`substring()` 메서드는 string 객체의 시작 index부터 종료 index 전까지 문자열의 부분 문자열을 반환한다.
