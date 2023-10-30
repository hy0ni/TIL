# 배열에서 최대값, 최소값 구하기

- Math.max(), Math.min()
- Function.prototype.apply() 사용하기
- Spread Operator(전개 연산자) 사용하기

## Math.max(), Math.min()

`Math.max()`  
Math.max() 함수는 입력값으로 받은 0개 이상의 숫자 중 가장 큰 숫자를 리턴한다.

`Math.min()`  
Math.min() 함수는 주어진 숫자들 중 가장 작은 값을 리턴한다.

```javascript
const maxValue = Math.max(1, 2, 3, 4, 5);
const minValue = Math.min(1, 2, 3, 4, 5);

console.log(maxValue); // 5
console.log(minValue); // 1
```

## Function.prototype.apply() 사용하기

```javascript
const arr = [1, 2, 3, 4, 5];
const maxValue = Math.max.apply(null, arr);
const minValue = Math.min.apply(null, arr);

console.log(maxValue); // 5
console.log(minValue); // 1
```

Function.prototype.apply() 메서드는 Javascript에서 함수를 호출하는 여러 가지 방법 중의 하나이다.  
일반적으로 함수를 호출할 때  
'함수명(파라미터)'의 형식으로 호출하지만,  
함수의 apply() 메서드를 호출하여 함수를 호출할 수도 있다.

`apply()` 메서드는 파라미터로,  
함수에서 사용할 this 객체와 호출하는 함수로 전달할 파라미터를 입력받는다.  
이때 apply() 메서드의 2번째 파라미터(호출하는 함수로 전달할 파라미터)는 배열 형태로 입력한다.

`Math.max.apply(null, arr)`  
Math.max() 함수의 apply() 메서드를 호출함.

apply() 메서드의 첫 번째 파라미터로  
Math.max() 함수 내부에서 사용할 this 객체를 전달해야 하는데,  
여기서는 따로 this 객체를 지정해 줄 필요가 없으므로 null을 전달한다.

apply() 메서드의 두 번째 파라미터로는  
Math.max() 함수로 전달할 파라미터를 배열 형태로 넣어주면 되는데,  
Math.max() 함수에 전달할 파라미터 5개 (1, 2, 3, 4, 5)를 배열 형태(arr)로 만들어 전달한다.

Math.max(), Math.min() 함수에 배열의 요소들을 풀어서 전달하기 위해  
apply() 메서드를 활용했다.

## Spread Operator(전개 연산자) 사용하기

```javascript
const arr = [1, 2, 3, 4, 5];
const maxValue = Math.max(...arr);
const minValue = Math.min(...arr);

console.log(maxValue); // 5
console.log(minValue); // 1
```

Spread Operator(전개 연산자)는 객체나 배열의 원소들을 하나씩 꺼내어서 펼쳐서 리턴한다.  
즉, Math.max(...arr)와 같이 작성해 주면  
Math.max(1, 2, 3, 4, 5)와 같이 실행되게 된다.

이 방법은 가독성이 좋음.
