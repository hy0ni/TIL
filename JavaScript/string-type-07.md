# replace() + 정규식 사용하여 대소문자 구분 없이 치환하기

```javascript
let str = "apple, Banana, orange";
let replaced_str = str.replace(/banana/i, "tomato");

console.log(str); // apple, Banana, orange
console.log(replaced_str); // apple, tomato, orange
```

대소문자의 구분없이 문자열을 치환하기 위해서 정규식(regular expression)을 사용한다.

정규식으로 찾으려는 문자열을 '/'로 감싸 파라미터로 들어가는 값이 정규식임을 알려주고,

'/' 뒤에는 'i'라는 modifier를 붙여준다.

**여기서 i는 대소문자를 구분하지 말라는 의미.**

'ignore case'라고 외우면 좀 더 기억하기 쉽다.
