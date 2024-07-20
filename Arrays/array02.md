> 유용한 배열 메서드

- [문자열을 배열로 변환하기](#문자열을-배열로-변환하기)
    - [- limit 사용](#--limit-사용)
    - [- 구분자가 없는 경우](#--구분자가-없는-경우)
    - [- 구분자가 문자열에 없는 경우](#--구분자가-문자열에-없는-경우)
- [배열을 문자열로 변환하기](#배열을-문자열로-변환하기)
  - [join()](#join)
    - [- 구분자를 지정하지 않은 경우](#--구분자를-지정하지-않은-경우)
    - [- 구분자 지정](#--구분자-지정)
    - [- 구분자를 공백으로 지정](#--구분자를-공백으로-지정)
    - [- 구분자로 빈 문자열 사용](#--구분자로-빈-문자열-사용)
    - [- 구분자로 "-" 사용](#--구분자로---사용)
  - [toString() 메서드](#tostring-메서드)
    - [- 중첩 배열 사용](#--중첩-배열-사용)
- [배열에 원소를 추가하고 제거하기](#배열에-원소를-추가하고-제거하기)
  - [push()](#push)
  - [pop()](#pop)
  - [unshift()](#unshift)
  - [shift()](#shift)

## 문자열을 배열로 변환하기

자바스크립트의 <b>split()</b> 메서드는 문자열에 사용되는 메서드입니다.  
split() 메서드는 문자열을 특정 구분자를 기준으로 나누어 배열로 변환하는 데 사용됩니다.

```javascript
// 구문
string.split(separator, limit);
```

- separator (필수): 문자열을 나눌 구분자입니다. 문자열이나 정규식을 사용할 수 있습니다.
- limit (선택): 반환할 배열의 최대 길이를 지정할 수 있습니다. 이 값을 지정하면 반환되는 배열의 요소 수가 이 값을 넘지 않습니다.

```javascript
const str = "apple,banana,orange";
```

문자열을 만듭니다.

```javascript
const arr = str.split(",");
console.log(arr); // ['apple', 'banana', 'orange']
```

콤마로 분리하면 문자열을 배열로 반환합니다.

```javascript
console.log(arr.length); //3
console.log(arr[0]); // 'apple'
console.log(arr[1]); // 'banana',
console.log(arr[2]); // 'orange'
console.log(arr[arr.length - 1]); // 'orange'
```

문자열이 배열로 변환됨을 확인할 수 있습니다.

#### - limit 사용

```javascript
const arr = str.split(",", 2);
console.log(arr); // ['apple', 'banana']
```

#### - 구분자가 없는 경우

```javascript
const str = "apple,banana";
const arr = str.split("");
console.log(arr); // ['a', 'p', 'p', 'l', 'e', ',', 'b', 'a', 'n', 'a', 'n', 'a']
```

전달되는 구분자가 없는 경우 각 문자는 개별 요소로 나누어 변환됩니다.

#### - 구분자가 문자열에 없는 경우

```javascript
const str = "applebanana";
const arr = str.split("");
console.log(arr); // ['a', 'p', 'p', 'l', 'e', 'b', 'a', 'n', 'a', 'n', 'a']
```

## 배열을 문자열로 변환하기

### join()

join() 메서드를 사용하면 배열을 다시 문자열로 만들 수 있습니다.  
자바스크립트의 join() 메서드는 배열의 모든 요소를 문자열로 결합하여 하나의 문자열로 반환합니다.  
각 요소는 지정된 구분자로 연결됩니다.  
join() 메서드는 원래 배열은 변경되지 않고 새 문자열을 반환합니다.

```javascript
// 구문
array.join(separator);
```

- separator (선택): 배열 요소를 결합할 때 사용할 구분자입니다.  
  이 값을 지정하지 않으면 기본 구분자인 쉼표(", ")가 사용됩니다.  
  (기본 구분자는 쉼표(", ")이지만, 원하는 구분자를 지정할 수 있습니다.)

#### - 구분자를 지정하지 않은 경우

```javascript
const arr = ["apple", "banana", "orange"];
const str = arr.join();
console.log(str); // "apple,banana,orange"
console.log(typeof str); // string
```

#### - 구분자 지정

```javascript
const arr = ["apple", "banana", "orange"];
const str = arr.join(",");
console.log(str); // "apple,banana,orange"
```

#### - 구분자를 공백으로 지정

```javascript
const arr = ["apple", "banana", "orange"];
const str = arr.join(" ");
console.log(str); // "apple banana orange"
```

#### - 구분자로 빈 문자열 사용

```javascript
const arr = ["apple", "banana", "orange"];
const str = arr.join("");
console.log(str); // "applebananaorange"
```

#### - 구분자로 "-" 사용

```javascript
const arr = ["apple", "banana", "orange"];
const str = arr.join("-");
console.log(str); // "apple-banana-orange"
```

### toString() 메서드

배열을 문자열로 변환하는 또 다른 방법으로 toString() 메서드를 사용할 수 있습니다.  
join()과 달리 구분자를 지정할 수 없으며, toString() 메서드는 항상 쉼표(", ")가 사용됩니다.  
원래 배열은 변경되지 않고 새 문자열을 반환합니다.

```javascript
const arr = ["apple", "banana", "orange"];
const str = arr.toString();
console.log(str); // "apple,banana,orange"
```

#### - 중첩 배열 사용

```javascirpt
const arr = ["apple", ["banana", "orange"], "mango"];
const str = arr.toString();
console.log(str) // "apple,banana,orange,mango"
```

중첩 배열의 요소도 쉼표로 구분되어 하나의 문자열로 변환됩니다.

## 배열에 원소를 추가하고 제거하기

### push()

push() 메서드는 <span style="background:#dcffe4;"><b>배열의 끝</b>에 하나 이상의 원소를 추가</span>합니다.
배열의 끝에 추가할 원소를 반드시 하나 이상 포함해야 합니다.

```javascript
const fruits = ["apple", "banana"];
fruits.push("orange");
console.log(fruits); // ["apple", "banana", "orange"]
```

메서드 호출이 완료되면 배열의 새 길이가 리턴됩니다.  
만약 새 배열의 길이를 변수에 저장하고 싶은 경우 다음과 같이 할 수 있습니다.

```javascript
const fruits = ["apple", "banana"];
const myArray = fruits.push("cherry");
console.log(myArray); // 3
```

### pop()

pop() 메서드는 <span style="background:#dcffe4;"><b>배열의 끝</b>에서 하나의 원소를 제거하고, 제거된 원소를 리턴</span>합니다.

```javascript
const fruits = ["apple", "banana", "cherry"];
fruits.pop();
console.log(fruits); // ['apple', 'banana']
```

메서드 호출이 완료되면 제거된 원소가 리턴됩니다.  
이 원소를 새 변수에 저장하기 위해서, 다음과 같이 할 수 있습니다.

```javascript
const fruits = ["apple", "banana", "cherry"];
const myArray = fruits.pop();
console.log(fruits); // ['apple', 'banana']
console.log(myArray); // 'cherry'
```

<b>unshift()와 shift()는 push(),pop()과 완전히 동일하게 동작합니다.  
다만 배열의 끝이 아닌 제일 처음 부분에 원소를 추가하거나 제거합니다.</b>

### unshift()

unshift() 메서드는 <span style="background:#dcffe4;"><b>배열의 시작</b>에 하나 이상의 원소를 추가</span>합니다.

```javascript
const fruits = ["apple", "banana"];
fruits.unshift("cherry");
console.log(fruits); //   ['cherry', 'apple', 'banana']
```

### shift()

shift() 메서드는 <span style="background:#dcffe4;"><b>배열의 시작</b>에서 하나의 원소를 제거하고, 제거된 원소를 리턴</span>합니다.

```javascript
const fruits = ["cherry", "apple", "banana"];
fruits.shift("cherry");
console.log(fruits); // ['apple', 'banana']
```
