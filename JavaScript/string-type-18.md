# 문자열 줄바꿈하기 (2가지 방법)

1. escape 문자 사용하기
2. 템플릿 리터럴(Template literals) 사용하기

## escape 문자 사용하기

```javascript
const str = "a\nb\nc\n";
console.log(str);
/* 
 a
 b
 c
 */
```

문자열에 New Line을 뜻하는 '\n' 이스케이프 문자를 넣어주면 줄바꿈이 가능하지만,  
가독성이 떨어지는 단점이 있다.

## 템플릿 리터럴(Template literals) 사용하기

```javascript
const str = `a
  b
  c`;
console.log(str);
/*
  a
    b
    c
  */
```

문자열을 정의할 때 따옴표 백틱(`)을 사용하면,
escape 문자를 사용하지 않아도, 입력한 그대로 문자열이 표현되기 때문에 여러 줄 표현도 가능함.

백틱을 이용하여 문자열을 표현하는 것을 템플릿 리터럴(Template literals)라고 함.

백틱을 입력할 때는 키보드의 왼쪽 상단(esc키 밑, 숫자 1왼쪽)의 키를 이용한다.
