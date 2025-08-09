# 3주차 내용 정리 및 중요 포인트

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