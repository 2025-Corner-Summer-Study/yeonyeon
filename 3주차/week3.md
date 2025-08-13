# 3주차 내용 정리 및 중요 포인트(1)-3,4회차

## 내용 배치

### float 사용...
- 블록 구조는 한 영역을 차지하므로 두 개가 나란히 존재 안하려함 (인라인 구조와 반대) 
- 블록 구조를 오른쪽을 정렬하려면 float 도움 필요
- BUT float은 치명적 약점 보유... float을 사용하면 특정 레이아웃이 잡혀야함
- (float 사용한 height값이 0으로 설정됨..영역 사라짐)
- 해결 방법 :
    - 1. 똑같이 float을 사용 (비추)
    - 2. clear: both; 을 사용 (비추)
    - 3. 상위 박스한테 overflow:hidden을 사용 (가끔씩 추천)
    - 4. clearfix를 만들어 사용(가장 많이 사용, 가장 추천)

### 정리
- 레이아웃 표현하려면 블록구조를 정렬해야함
- float을 사용하면 height값을 인식 못하는 문제점이 생김
- 그래서 4가지 방법 중 가장 추천하는 건 overflow와 clearfix
- overflow가 쓰기 편하나, 2단 메뉴부분이나, 드롭다운 메뉴에서는 사용 불가
- clearfix 가장 추천

### clearfix
- float를 사용하면 영역 깨짐을 방지하기 위한 방법
- float을 사용한 상위 박스에 .clearfix를 설정하면 영역이 무너지지 않고 잡힘
- display를 블럭으로 설정해서 가상요소 (content) 만들고 line-height를 0으로 만들어야 함

```css
.clearfix: before;, .clearfix:after{
    display: block;
    content: '';
    line-height:0;
}

.clearfix:after{
    clear: both;
}

```

### 번외
- chatGpt를 사용한 결과 clearfix는 아직도 사용은 하나 필수로는 사용 x
- 예전에는 float 붕 뜨는 문제를 해결하려 clearfix를 썼으나,
- 현재는 flexbox나 grid가 표준처럼 쓰이고 있어 float자체를 잘 안씀
- 대체로는 overflow:auto;나 display:flow-root; 사용

## 이미지
- img 태그와 background-image 속성을 통해 표현 가능
- 의미 O-> img태그
- 의미 x-> CSS 속성(=background-image)
- 의미 있어도 CSS속성으로 표현 가능
- background를 통해 이미지 표현하면 대체 문자 표현 불가, IR 기법은 대체 텍스트 제공

### IR 기법
- Phark Method: 의미 있는 이미지의 대체 텍스트 제공하는 경우
    =>img로 대체할 element의 배경이미지를 설정하고 글자는 text-indent를 이용해 화면 바깥으로 빼내어 보이지 않게 하는 방법 
- WA IR: 의미 있는 이미지의 대체 텍스트로 이미지를 off시에도 대체 텍스트를 보여주려고 할 때
    => 이미지로 대체할 엘리먼트에 배경이미지를 설정하고 글자는 span태그로 감싼 후 z-index-1을 이용하여 화면에 안보이게 처리
- Screen Out: 대체 텍스트가 아닌 접근성을 위한 숨김 텍스트를 제공할 때
    => 이미지로 대체할 엘리먼트에 배경이미지를 설정하고 글자는 화면 바깥으로 빼내고 위치는 절대 위치를 통해 위치를 숨길 경우


```css
/*Phark Method 코드 예시*/
.ir_pm{
    display:block;
    overflow: hidden;
    font-size:0;
    line-height:0;
    text-indent:-9999px; /*화면 바깥으로 꺼내는 것*/
}

/*WA IR 코드 예시*/
.ir_wa{
    display:block;
    overflow: hidden;
    position: relative;
    z-index:-1;
    width:100%;
    height:100%;
}

/*Screen Out 코드 예시*/
.ir_su{
    overflow: hidden;
    position:absolute;
    width:0;
    height:0;
    line-height:0;
    text-indent:-9999px;
}
```
### 결론
- 의미가 있는 이미지를 background 속성으로 표현할 경우 대체 문자 표현을 위해 IR 기법 사용
- IR 기법은 여러가지 방법이 있지만 Phark Method, WA IR, Screen Out 이 세가지를 가장 많이 사용
- 백그라운드로 이미지를 표현하는 이유는 이미지 스프라이트 기법을 이용하기 때문

### 번외
- 강의 내용상으론 그렇고 현재는 IR기법 자체를 잘 안쓴다고 함 
- img alt, SVG, ARIA를 더 대체해서 많이 사용한다고 함


## 몰랐던 기능
- transition: 마우스로 각 태그로 이동할 때 변하는 속도 조절
- 기준점 설정: position: relative사용