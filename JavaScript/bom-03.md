# 현재 페이지 URL 가져오기

## window.location (Location 객체)

window.location 속성에 접근하면 Location 객체에 접근할 수 있는데
이 Location 객체의 속성들을 사용해서 현재 페이지의 URL 정보를 알아낼 수 있다.

**`window.location.href`**  
전체 URL 문자열을 가져온다.

**`window.location.protocol`**  
마지막 ':'를 포함한 프로토콜 정보를 가져온다.

**`window.location.host`**  
URL의 호스트 정보를 가져온다.  
만약 URL에 포트번호가 있으면 ':'과 포트번호를 포함한다.

**`window.location.hostname`**  
URL의 호스트명을 가져온다.  
이 값은 ':'과 포트번호를 포함하지 않는다.

**`window.location.port`**  
URL의 포트 번호

**`window.location.pathname`**  
hostname 뒤의 '/'문자 뒤의 경로를 가져온다.

**`window.location.search`**  
'?' 뒤의 쿼리스트링을 가져온다.
