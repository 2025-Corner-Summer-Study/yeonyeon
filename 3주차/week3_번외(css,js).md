# 강의를 위한 css, javascript 복습

## CSS 번외

### 가상 클래스 선택자
- :link -> 방문하지 않은 링크에 스타일 적용
- :visited -> 방문한 링크에 스타일을 적용
- :hover -> 특정 요소에 마우스 포인터 올리면 스타일 적용
- :active -> 웹 요소를 활성화했을 때 스타일을 적용
- :checked -> 선택한 항목의 스타일을 적용
- :first-child -> 여러 요소 중에서 첫 번재 자식 요소
- :last-child ->  여러 요소 중에서 마지막 자식 요소
- :is -> 같은 스타일을 여러 요소에 적용할 때 is 가상 선택자로 묶어서 표현 가능
```css
:is(h1,h2,h3){
    color:red;
}
```
- :has -> A:has(B)라 할때 A요소가 괄호안의 B요소를 가지고 있는지 체크

```css
nav a:hover{
    color:#ff7a18;
}
/*1.nav요소에 a:hover 선택자가 있다면  2. :hover 선택자가 적용되지 않는 요소를 선택택*/
nav:has(a:hover) a:not(:hover){
    opacity:0.3; /*opacity: 요소를 불투명하게 만듦(0-1)*/
}
```

### 트랜지션 (transition)
- 웹 요소의 배경색을 바꾸거나 도형의 테두리를 사각형에서 원형으로 바뀌는 것처럼 속성이 바뀜
- 표기: transition: /transition-property값/ /transition-duration값/ /transition-timing-function값/ /transition-delay 값/ 
    - transition-property -> all, none, 속성이름
    - transiton-duration -> 시간
    - transition-timing-function -> linear, ease, ease-in, ease-out, ease-in-out, cubic-beizer(n,n,n,n)

## Javascript 번외

### 화살표 함수
- 함수 이름이 없을 경우에만 사용 가능
```javascript
const hi= () => {return "안녕하세요"};

let hi= user => {document.write('${user}님 안녕하세요?')};

let sum= (a,b) =>a+b;
```

### 이벤트

#### 마우스
- click: 사용자가 HTML요소를 클릭할 때 이벤트 발생
- mousedown : 사용자가 요소 위에서 마우스 버튼을 눌렀을 때 이벤트 발생
- mouseover: 마우스포인터가 요소 위로 옮겨질 때 이벤트 발생
#### 키보드
- keydown: 사용자가 키를 누르는 동안 이벤트 발생
- keypress: 사용자가 키를 눌렀을 때 이벤트 발생
- keyup: 사용자가 키에서 손을 뗄 때 이벤트 발생
#### 문서
- error: 문서가 정확히 로딩되지 않았을 때 이벤트 발생
- load: 문서 로딩이 끝나면 이벤트 발생
- scroll: 문서 화면이 스크롤되었을 때 이벤트 발생
#### 폼
- change: 목록이나 체크 상태 등이 변경되면 이벤트가 발생함-input, select, textarea 태그에서 사용
- focus: 폼 요소에 포커스놓였을 때 이벤트 발생 - label, select, texxtarea, button 태그에서 사용
- reset: 폼이 리셋되었을 때 이벤트 발생
- submit: submit 버튼을 클릭했을 때 이벤트 발생

### window 객체의 메서드
- alert(): 알림 창을 표시
- confirm(): [확인], [취소] 버튼이 있는 확인 창 표시
- open(): 새로운 창 열기
- close(): 현재 창을 닫음
    ->ex. button onclick="javascript: window.close();"
- stop(): 로딩 중지

 #### 새 브라우저 창 여는 open()메서드
 
 window.open(경로, 창 이름, 창 옵션)
 - 경로: 팝업창에 표시할 문서나 사이트 경로 나타냄
 - 창 이름: 팝업 창의 이름을 지정하면 항상 이 창에 팝업 내용이 나타나도록 할 수 있음. 이름 미지정시 팝업창이 계속 새로 나타남
 - 창 옵션: left, top 속성을 사용해 위치를 정하거나 width, height 속성을 사용해 크기 지정 가능. 위치 미지정시 팝업창은 화면의 맨 왼쪽 위에 나타남
 
 ```javascript
 window.open("notice.html", "", "width=500, height=400");
 // 너비가 500px, 높이가 400px인 팝업창
 ```

### DOM
- getElement
    - getElementById -> document.getElementById("id명")
    - getElementByClassName ->document.getElementByClassName("class명")
    - getElementsByTagName ->document.getElementByTagName("태그명")
- queryselector
    - 하나만 집어내는 셀렉터
    - document.querySelector('#heading')
    - document.querySelector('img') -> 이미지가 4개 있다고 가정했을 시 가장 첫번째 것만 가져옴
        - 만약 다 가져오고 싶다면..? querySelectorAll 사용