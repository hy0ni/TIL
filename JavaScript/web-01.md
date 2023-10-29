# url 리다이렉트(Redirect), location.href 와 location.replace 차이점

- 리다이렉트(Redirect)
- Redirect 사용하는 이유
- HTML Redirect
- javascript Redirect
- location.href 와 location.replace 차이점

## 리다이렉트(Redirect)

쉽게 말해 다른 페이지로 연결되는 것을 말한다.

## Redirect 사용하는 이유

기업 입장에서 여러 상황에 대응하기 위해 리디렉션을 사용한다.
예를 들어 사이트의 상호를 변경한 경우, 웹 사이트 두 개가 하나로 합쳐진 경우, 업데이트된 콘텐츠로 트래픽을 유도하는 경우 등에 사용한다.

## HTML Redirect

meta 태그에 작성하는 방식이 자바스크립트 방식보다 우선순위가 높다.
하지만 이 방식은 브라우저에서 뒤로 가기 버튼을 누른 경우 이전 페이지 이동이 불가하기 때문에 지양해야 하는 방법이기도 하다.

```html
<head>
  <meta http-equiv="refresh" content="2; URL='url'" />
</head>
```

content 뒤에 있는 숫자 2는 페이지가 로딩되고 2초 후에 갱신된다는 것이고,
URL은 갱신할 때 읽어 들일 페이지의 주소이다.

## javascript Redirect

```html
window.location.href = "url";
```

window.location 프로퍼티에 값을 설정해서 만들어지며, 새로운 페이지가 로드된다.

```html
window.location.replace("url");
```

현재 페이지를 새로운 페이지로 덮어 씌울 때 사용한다.

## location.href 와 location.replace 차이점

| 항목                | location.href                                                      | location.replace                                                                                                                                  |
| ------------------- | ------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| 용도                | 새로운 페이지로 이동<br>(url을 이동하는 대부분의 경우에 사용된다.) | 기존페이지를 새로운 페이지로 변경<br>(뒤로가기시 이전 페이지로 가는 것을 차단할 경우 사용된다. 방문 히스토리를 남기지 않아야 하는 경우 사용된다.) |
| 타입                | 속성                                                               | 메써드(함수)                                                                                                                                      |
| 웹브라우저 히스토리 | 저장됨                                                             | 저장되지 않음                                                                                                                                     |
| 브라우저 뒤로가기   | "location.href" 호출한 페이지로 이동                               | location.replace()" 호출한 페이지로 뒤로가기 이동 불가. 웹브라우저 히스토리에 있는 가장 최근 이전 페이지로 이동.                                  |
| 사용 예)            | location.href = "url";                                             | location.replace("url");                                                                                                                          |
