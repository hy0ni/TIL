> 조건문

- [if ... else 문](#if--else-문)
- [else if](#else-if)
- [비교 연산자](#비교-연산자)
- [if ... else 중첩](#if--else-중첩)
- [논리 연산자: AND, OR 그리고 NOT](#논리-연산자-and-or-그리고-not)

## if ... else 문

자바스크립트에서 가장 일반적인 형태의 조건문.

```javascript
if (조건) {
  // 만약 조건(condition)이 참일 경우 실행할 코드
  코드 A
} else {
  // 대신 실행할 다른 코드
  코드 B
}
```

만약 조건이 true면, 코드 A를 실행하고, 아니면 코드 B를 실행한다.

```javascript
if (조건) {
  만약 조건(condition)이 참일 경우 실행할 코드
}

실행할 다른 코드
```

반드시 else와 두 번째 중괄호를 포함하지 않아도 되지만,
여기서 조심해야 할 점은 코드의 두 번째 블록은 조건문에 의해서 제어되지 않으므로, 조건이 true나 false를 리턴하는 것과 관계없이 항상 동작합니다.

```javascript
if (조건) 만약 조건(condition)이 참일 경우 실행할 코드
else 대신 실행할 다른 코드
```

위 코드는 유효한 코드이지만,가독성을 위해 사용하는 것을 추천하지 않습니다.

## else if

else if문은 여러 조건을 순차적으로 검사할 때 사용할 수 있습니다.

```javascript
let score = 85;
if (score >= 90) {
  console.log("A 학점");
} else if (score >= 80) {
  console.log("B 학점");
} else if (score >= 70) {
  console.log("C 학점");
} else if (score >= 60) {
  console.log("D 학점");
} else {
  console.log("F 학점");
}
// result: B 학점
```

score 값에 따라 다른 학점을 출력합니다.  
score가 90 이상일 경우 "A 학점"을 출력하고, 80 이상 90 미만일 경우 "B 학점"을 출력하는 식으로 조건을 검사합니다.  
각 조건이 만족하지 않으면 다음 else if 조건으로 넘어가며, 모든 조건이 만족하지 않으면 else 문이 실행되어 "F 학점"을 출력합니다.

이렇게 여러 조건을 순차적으로 검사하여 적절한 코드를 실행할 수 있습니다.

## 비교 연산자

비교 연산자는 조건문 안의 조건을 테스트하는데 사용됩니다.

- `===와 !==` 한 값이 다른 값과 같거나 다른지 테스트한다.
- `< 와 >` 한 값이 다른 값보다 작은지 큰지 테스트한다.
- `<= 와 >=` 한 값이 다른 값보다 작거나 같은지, 크거나 같은지 테스트한다

## if ... else 중첩

나이를 기반으로 성인, 청소년, 어린이를 구분하여 다른 메시지를 출력하는 예시로 설명합니다.

```javascript
let age = 20;

if (age >= 18) {
  if (age >= 65) {
    console.log("노인입니다.");
  } else {
    console.log("성인입니다.");
  }
} else {
  if (age >= 13) {
    console.log("청소년입니다.");
  } else {
    console.log("어린이입니다.");
  }
}
```

1. age가 18 이상일 경우:

- 다시 age가 65 이상인지 검사하여 "노인입니다."를 출력합니다.
- 그렇지 않으면 "성인입니다."를 출력합니다.

2. age가 18 미만일 경우:

- 다시 age가 13 이상인지 검사하여 "청소년입니다."를 출력합니다.
- 그렇지 않으면 "어린이입니다."를 출력합니다.

이런 식으로 if ... else 문을 중첩하여 더 복잡한 조건을 처리할 수 있습니다.

## 논리 연산자: AND, OR 그리고 NOT

만약 중첩된 if...else문 작성 없이 다양한 조건을 테스트하길 원한다면 논리 연산자를 사용할 수 있습니다.

- AND 연산자 (&&)  
  AND 연산자는 두 조건이 모두 참일 때 참을 반환합니다. 하나라도 거짓이면 거짓을 반환합니다.

```javascript
let a = true;
let b = false;

if (a && b) {
  console.log("둘 다 참입니다.");
} else {
  console.log("하나 이상이 거짓입니다.");
}
// result: "하나 이상이 거짓입니다."
```

a는 true이고 b는 false이므로 a && b는 false입니다.

- OR 연산자 (||)  
  OR 연산자는 두 조건 중 하나라도 참이면 참을 반환합니다. 둘 다 거짓일 때만 거짓을 반환합니다.

```javascript
let a = true;
let b = false;

if (a || b) {
  console.log("하나 이상이 참입니다.");
} else {
  console.log("둘 다 거짓입니다.");
}
// result: "하나 이상이 참입니다."
```

a는 true이고 b는 false이므로 a || b는 true입니다.

- NOT 연산자 (!)  
  NOT 연산자는 단일 조건을 반전시킵니다. 조건이 참이면 거짓을, 거짓이면 참을 반환합니다.

```javascript
let a = true;

if (!a) {
  console.log("a는 거짓입니다.");
} else {
  console.log("a는 참입니다.");
}
// result: "a는 참입니다."
```

a는 true이므로 !a는 false가 됩니다.

논리 연산자를 결합하여 복잡한 조건을 검사할 수 있습니다.

```javascript
let age = 25;
let hasTicket = true;

if (age >= 18 && hasTicket) {
  console.log("입장할 수 있습니다."); // result: "입장할 수 있습니다."
} else {
  console.log("입장할 수 없습니다.");
}

let isMember = false;

if (age >= 18 || isMember) {
  console.log("할인을 받을 수 있습니다."); // result: "할인을 받을 수 있습니다."
} else {
  console.log("할인을 받을 수 없습니다.");
}

if (!isMember) {
  console.log("회원이 아닙니다."); // result: "회원이 아닙니다."
} else {
  console.log("회원입니다.");
}
```

위 예시에서는 AND, OR, NOT 연산자를 사용하여 여러 조건을 결합하고 검사합니다.
