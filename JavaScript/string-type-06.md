# 문자열에서 특정 문자열 치환하기

- replace()
- replace() 함수는 첫 번째로 찾은 문자열만 치환해 준다.
- replace() 함수는 대소문자를 구분한다.

## replace()

```javascript
string.replace(searchValue, newValue);
```

searchValue, newValue를 파라미터로 입력받고 문자열에서 searchValue를 찾아서 newValue로 치환한다.

```javascript
let str = "apple, banana, orange";
let replaced_str = str.replace("banana", "tomato");

console.log(str); // apple, banana, orange
console.log(replaced_str); // apple, tomato, orange
```

`replace()` 함수는 원본 문자열을 변경하지 않고,<br>
'banana'가 'tomato'로 치환된 문자열을 리턴한다.

## replace() 함수는 첫 번째로 찾은 문자열만 치환해 준다.

```javascript
let str = "apple, banana, orange, banana";
let replaced_str = str.replace("banana", "tomato");

console.log(str); // apple, banana, orange, banana
console.log(replaced_str); // apple, tomato, orange, banana
```

replace() 함수는 문자열에서 첫 번째로 찾은 문자열만 치환해 주므로,
첫 번째 'banana'만 'tomato'로 치환되고,
두 번째 'banana'는 그대로인 것을 확인할 수 있다.

## replace() 함수는 대소문자를 구분한다.

```javascript
let str = "apple, Banana, orange";
let replaced_str = str.replace("banana", "tomato");

console.log(str); // apple, Banana, orange
console.log(replaced_str); // apple, Banana, orange
```

원본 문자열은 'banana'를 포함하고 있지 않으므로,<br>
'banana'를 찾아서 변경하려 시도해도 변경되지 않는다.
