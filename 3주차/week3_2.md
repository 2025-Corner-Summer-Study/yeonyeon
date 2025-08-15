# 3주차 내용 정리 및 중요 포인트(1)-5,6회차(유튜브기준)

## 미디어쿼리
- 반응형 웹페이지를 제작하려면 뷰포트와 미디어쿼리 사용 필요
- 뷰포트 -> PC 화면 비율을 모바일 비율로 바꿔줌
- 미디어쿼리 -> 화면 크기에 따라 CSS 제작
    - @media[only/not][mediatype][and/,](조건문){실행문}
        - @media : 미디어쿼리 시작 의미
        - only / not: only는 미디어쿼리를 지원하는 브라우저에서만 해석, not은 반대 (생략 가능)
        - mediatype : 미디어 유형 설정 (생략 가능)
        - and/, : and는 둘다 조건에 맞아야 하고 ,는 하나만 맞아도 실행 (and/or 개념) (생략 가능)
        - 조건문/ 실행문 : 화면 크기의 조건을 설정하고 그에 따른 실행문을 작성 
    - 미디어쿼리 적용 방법
        - 외부링크에서 사용  -> link rel="stylesheet" href="style.css"  ==> 가장 많이 사용
        - 화면 크기별로 CSS 작성 -> link rel="stylesheet" media="all and~~
        - 임포트 시키기 ->@import url(style.css) all and ~
        

