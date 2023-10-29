# 마우스 클릭 좌표

- screenX, screenY
- pageX, pageY
- clientX, clientY
- offsetX, offsetY

## screenX, screenY

사용자 모니터 화면을 기준 왼쪽 상단 모서리가 (0, 0)이 된다.

## pageX, pageY

전체 문서를 기준으로 좌표를 표시한다.
만약 문서를 표현할 때 스크롤이 생긴다면,
특정 지점의 pageY 좌표값은 페이지가 스크롤 될 때마다 변경된다.

## clientX, clientY

브라우저에서 사용자에게 웹페이지가 보여지는 영역을 기준으로 좌표를 표시한다.
스크롤바가 움직이더라도, 특정 지점의 clientX, clientY의 값은 동일하다.

## offsetX, offsetY

좌표를 출력하도록 하는 이벤트가 걸려있는 DOM node를 기준으로 좌표를 표시한다.

만약 특정 div 영역에서 offsetX, offsetY를 출력한다면,
div의 왼쪽 상단 모서리 부분이 offsetX, offsetY의 값(0, 0)이 된다.
