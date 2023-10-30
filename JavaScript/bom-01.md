# 절대값 구하기 Math.abs()

## Math.abs()

```javascript
Math.abs(x);
```

Math.abs() 함수는` 주어진 숫자의 절대값을 반환`한다.  
x가 양수이거나 0이라면 x를 리턴하고, x가 음수라면 x의 반대값, 즉 양수를 반환한다.

```javascript
Math.abs(-10); // 10
Math.abs(-10.123); // 10.123
Math.abs(10); // 10
Math.abs("-2"); // 2
```

파라미터로 입력받은 숫자의 절대값을 반환한다.

```javascript
Math.abs(""); // 0
```

빈 문자열이 입력되면 0을 리턴한다.

```javascript
Math.abs(true); // 1
Math.abs(false); // 0
```

boolean 값이 입력되면 true인 경우 1, false인 경우 0을 리턴한다.

```javascript
Math.abs(null); // 0
```

null이 입력되면 0을 리턴한다.

```javascript
Math.abs(undefined); // NaN
```

undefined 값이 입력되면 NaN(Not a Number)을 리턴한다.

```javascript
Math.abs("apple"); // NaN
```

숫자로 변환할 수 없는 문자열이 입력되면 NaN(Not a Number)을 리턴한다.
