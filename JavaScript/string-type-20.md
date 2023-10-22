# 문자열에서 마지막 콤마 제거하기

## replace()

`replace()` 함수는 문자열에서 첫 번째 파라미터 값을 찾아서,
두 번째 파라미터 값으로 변환한다.
이때, 첫 번째로 찾은 값만 변환한다.

```javascript
const str1 = "apple, banana";
const str2 = "apple, banana,";
const str3 = "apple, banana,    ";
console.log(str1.replace(/,\s*$/, "")); // apple, banana
console.log(str2.replace(/,\s*$/, "")); // apple, banana
console.log(str3.replace(/,\s*$/, "")); // apple, banana
```

`정규식(/,\s*$/)`에 해당하는 값을 찾아서, `빈 공백("")`으로 변환해 준다.

### 정규식(/,\s\*$/)

- `/` : 정규식 전체를 둘러싸고 있는 '/'는 정규식의 시작과 끝을 표시.
- `,` : 찾고자 하는 콤마(,) 문자.
- `\s` : space 나 tab과 같은 공백을 나타냄.
- `*` : 0번 이상을 의미.
- `$` : 문자열의 끝을 의미.

위 정규식은 문자열의 끝에서 콤마와 0번 이상의 공백이 있는 경우를 찾는다.<br>
replace() 함수는 정규식에서 찾은 '콤마와 0번 이상의 공백'을 ""(비어있는 문자열)로 치환한다.
