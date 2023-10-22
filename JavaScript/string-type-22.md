# 배열인지 확인하기 isArray()

## isArray()

```javascript
Array.isArray(obj);
```

Array.isArray() 메서드는 인자가 Array인지 판별한다.

```javascript
Array.isArray([1, 2, 3]); // true
Array.isArray({ foo: 123 }); // false
Array.isArray("foobar"); // false
Array.isArray(undefined); // false
Array.isArray(null); // false
```

파라미터로 입력받은 객체가 배열이면 true,<br>
배열이 아니면 false를 리턴함.
