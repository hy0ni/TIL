### 오늘 배운 것

`명명 규칙`  
업데이터 함수 인수의 이름은 해당 state 변수의 첫 글자로 지정하는 것이 일반적이다.
```javascript
setEnabled(e => !e);
setLastName(ln => ln.reverse());
setFriendCount(fc => fc * 2);
```
좀 더 자세한 코드를 선호하는 경우   setEnabled(enabled => !enabled)와 같이 전체 state 변수 이름을 반복하거나,  
setEnabled(prevEnabled => !prevEnabled)와 같은 접두사를 사용하는 것이 널리 사용되는 규칙이다.

React 도큐먼트 정독중  
[state를 사용해 input 다루기](https://ko.react.dev/learn/reacting-to-input-with-state)
까지 공부함.
