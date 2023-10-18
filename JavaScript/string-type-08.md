# 모든 문자열 치환하기 replaceAll()

## replaceAll()

`replaceAll()` 함수는 전달된 문자열과 일치하는 모든 문자열을 대체 문자열로 대체된 새 문자열을 반환한다. <br>
원본 문자열은 변경되지 않고 그대로 유지된다.

```javascript
const str = "apple, banana, banana, banana";

console.log(str.replaceAll("banana", "orange")); // apple, orange, orange, orange
console.log(str); // apple, banana, banana, banana
```

`str.replaceAll("banana", "orange")`
모든 "banana" 문자열을 찾아서 "orange"로 대체하여 리턴.<br>
이때 원본 문자열은 변경되지 않는다.

## 대소문자 구분 없이 모든 문자열 치환하기

**replaceAll() + 정규식 사용**

```javascript
const regex = /Banana/gi;

console.log(str.replaceAll(regex, "cherry")); // apple, cherry, cherry, cherry
```

정규식으로 찾으려는 문자열을 '/'로 감싸 파라미터로 들어가는 값이 정규식임을 알려준다.<br>
'/' 뒤에는 'i'라는 modifier를 붙여준다.
