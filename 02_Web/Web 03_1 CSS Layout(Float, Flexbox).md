# Layout

- 웹 페이지에 대한 포함되는 요소들을 어떻게 취합하고 그것들이 어느 위치에 놓일 것인지를 제어

#### CSS page layout techniques

- **Display**
- **Position**
- **Float**
- **Flexbox**
- **Gride system**
- Table layout
- Multiple-column layout



## Float

- 한 요소(element)가 정상 흐름(normal flow)으로부터 빠져 <br>텍스트 및 인라인(inline)요소가 그 주위를 감싸 <br>요소의 좌, 우측을 따라 배치되어야 함을 지정<br>(**block 요소는 아님**)
- 본래는 이미지 좌, 우측 주변으로 텍스트를 둘러싸는 레이아웃(신문 등)을 위해 도입
  - 좌측 사진, 우측 글이면 float left
  - 우측 사진, 좌측 글이면 float right
- 더 나아가 이미지가 아닌 다른 요소들에도 적용해 웹 사이트의 전체 레이아웃을 만드는 데까지 발전



### 속성

- **none**: 기본값
- **left**: 요소를 왼쪽으로 띄움
- **right**: 요소를 오른쪽으로 띄움

```CSS
<style>
  .box {
    width: 150px;
    height: 150px;
    border: 1px solid black;
    background-color: crimson;
    margin: 20px;
  }

  .left {
    float: left;
  }

  .right {
    float: right
  }
</style>
</head>

<body>
  <div class="box left">float left</div>
  <div class="box left">float left</div>
  <div class="box right">float right</div>
  <p>장문의 텍스트</p>
```

- float을 쓰면 다른 요소 위에 겹쳐짐

```css
  <style>
    .box1 {
      width: 150px;
      height: 150px;
      border: 1px solid black;
      background-color: crimson;
      color: white;
      text-align: center;
      line-height: 150px;
    }

    .box2 {
      width: 300px;
      height: 150px;
      border: 1px solid black;
      background-color: blue;
      color: white;
      text-align: center;
      line-height: 150px;
    }

    .left {
      float: left;
    }
  </style>
</head>
<body>
  <div class="box1 left">div</div>
  <div class="box2">div</div>
```

- float를 하더라도 다른 요소가 못 오게 투명한 요소를 추가하는 것이<br>**Float clear**

```css
    .clearfix::after {
      content="";
      display: block;
      clear: both
    }
  </style>
</head>
<body>
  <div class="clear-fix">
    <div class="box1 left">div</div>
  </div>
  <div class="box2">div</div>
```

- 위처럼 하면 box1 밑에 가상요소가 생성되고 box2는 올라가지 못함
- float 요소의 부모 요소에 설정
- clear 속성을 추가 안하면 가상요소도 위로 올라가는것을 막기 위함

### Float clear - 가상요소

```css
.clearfix::after {
  content: "";
  display: block;
  clear: both;
}
```

- `::after` 
  - [MDN에서 확인하기](https://developer.mozilla.org/ko/docs/Web/CSS/::after)
  - 선택한 요소의 맨 마지막 자식으로 **가상 요소**(**의사요소**)를 하나 생성
  - 보통 content 속성과 함께 짝지어, 요소에 장식용 콘텐츠를 추가할 때 사용
  - 기본값은 inline
  - `clear` 
    - 선행 floating 요소 다음일 수있는지 또는 그 아래로 내려가(해제되어(cleared))야 하는 지를 지정
    - clear 속성은 float 및 비float 요소 모두에 적용됨
- 정리
  - flexbox 및 그리드 레이아웃과 같은 기술이 나오기 이전에<br>Float은 열 레이아웃을 만드는데 사용됨
  - flexbox와 grid의 출현과 함께 결국 원래 텍스트 블록 내에서 float 이미지를 위한 열할로 돌아감
    - MDN에서는 더 새롭고 나은 레이아웃 기술이 나와있으므로 "레거시 레이아웃 기술"로 분류
  - 웹에서는 여전히 사용하는 경우도 있음(ex. naver nav bar)



## Flexbox

### CSS Flexible Box Layout = Flexbox

- 참고 사이트: [네이버 D2](https://d2.naver.com/helloworld/8540176),  [css tricks](https://css-tricks.com/)

- 오랫동안 CSS Layout을 작성할 수 있는 도구는 float 및 positioning뿐이었음
  - 문제가 있는 것은 아니지만, 어떤 면에서는 제한적이고 한계가 있음
- Flexbox라 불리는 Flexible Box module은 
  - Flexbox 인터페이스 내의 아이템 간 
  - "공간배분"과 편리한 "정렬"기능을 제공하기 위한 1차원 레이아웃으로 설계

- 즉, 요소 간 공간 배분과 정렬 기능을 위한 1차원(단반향) 레이아웃



- 크게 딱 2가지만 기억하자. **요소와 축**!

- 요소

  - Flex Contatiner (부모 요소): 큰박스안에
  - Flex Item (자식 요소): 작은박스 있음

- 축

  - main axis (메인축): 방향설정에 따라 x 또는 y축(기본은 x축)
    - 기본값일 때(x축 가로)
    - main start 축 왼쪽, 반대쪽은 main end
    - cross start 축 위쪽, 반대쪽은 cross end
  - cross axis (교차축): 메인축에 수직으로 교차하는 축

  

### Flexbox의 구성요소

- Flex Container (부모 요소)
  - flexbox 레이아웃을 형성하는 가장 **기본**적인 모델
  - Flex Item들이 놓여있는 영역
  - display 속성을 `flex` 또는 `inline-flex`로 지정
- Flex Item (자식 요소)
  - container의 컨첸츠



### Flexbox 시작

```css
.flex-contatiner {
  display: flex;
}
```

- 부모 요소에 `display: flex;` 혹은`display: inline-flex;`를 작성하는 것부터 시작



### Flex에 적용하는 속성

- 배치 **방향** 설정(메인 축 방향 4가지)
  - flex-direction 
- 메인축 방향 **정렬**
  - justify-content
  - justify에 self, items가 없는 이유
    - auto margins로 쉽게 정렬하기 때문에 메인축에서 필요가 없음
    - 특정 요소에서 `margin-left: auto;`로 우측정렬을 쉽게 할 수 있음
    - [w3c 'auto-margins' 참고](https://www.w3.org/TR/css-flexbox-1/#auto-margins)
- 교차축 방향 **정렬**
  - align-items(다른 것보다 잘 씀), align-self, align-content
- 기타
  - flex-wrap, flex-flow, flex-grow, order

#### flex-direction

- main-axis 방향만 바뀜(4가지)
- flexbox는 단방향 레이아웃이기 때문
  - row(**default**) 좌에서 우로
  - row-reverse 우에서 좌로
  - column 위에서 아래로
  - column-reverse 아래에서 위로

#### justify & align

- justify
  - 메인축 정렬(설정에 따라 가로 또는 세로)
- align
  - 교차축 정렬

#### content & items & self

- content
  - 여러줄
- items
  - 한줄
- self
  - flex item 개별 요소를 선택
- 예시
  - justify-content: 메인축 기준 여러 줄 정렬
  - align-items: 교차축 기준 한 줄 정렬
  - align-self: 교차축 기준 선택한 요소 하나 정렬



- justify-content
  - flex-start, flex-end, center, space-between, space-around, space-evenly
- align-items
  - flex-start, flex-end, center, stretch, baseline
- align-content
  - flex-start, flex-end, center, stretch, space-between, space-around
- align-self
  - auto, flex-start, flex-end, center, baseline, stretch

#### 예시(한 줄 정렬)

- flex에서 가장 처음에 해야 하는 것

  - flex container 선언

  ```css
    <style>
      .flex-container {
        display: flex;
      }
    </style>
  
  
      <div class="box flex-container">
        <div class="item1">1</div>
        <div class="item2">2</div>
        <div class="item3">3</div>
        <div class="item4">4</div>
        <div class="item5">5</div>
        <div class="item6">6</div>
        <div class="item7">7</div>
        <div class="item8">8</div>
        <div class="item9">9</div>
        <div class="item10">10</div>
        <div class="item11">11</div>
        <div class="item12">12</div>
        <div class="item13">13</div>
      </div>
  ```

  - 위에서 아래로 배치된 박스 13개에서
  - flex 설정하면 기본값(좌에서 우로)으로 정렬됨
  - `inline-flex`로 하면 요소 크기만큼만 차지

### 정리

#### display: flex

- **정렬하려는 부모 요소에 작성**
- inline-flex: flex 영역을 블록으로 쓰지 않고 인라인 요소로 사용
- flex 선언 시 아래 사항들이 기본 값으로 지정됨
  - itme은 행으로 나열
  - item은 메인축의 시작부터 정렬
  - item은  교차축의 크기를 채우기 위해 늘어남
  - flex-wrap속성을 nowrap으로 지정

#### flex-direction

- item이 쌓이는 방향 설정
- main-axis를 변경
- row(기본값): 주축의 방향이 왼쪽에서 오른쪽
- row-reverse: 주축의 방향이 오른쪽에서 왼쪽
- column: 주축의 방향이 위에서 아래
- column-reverse: 주축의 방향이 아래에서 위

#### flex-wrap

- 요소들이 강제로 한 줄에 배치 되게 할 것인지 여부 설정
- nowrap (**기본값**): 모든 아이템들 한 줄에 나타내려고 함
  - 그래서 자리가 없어도 튀어나옴
- wrap: 넘치면(화면 넘어가면) 그 다음 줄로
- wrap-reverse: 넘치면(화면 넘어가면) 그 윗줄로(역순)

#### flex-flow

- flex-direction 과 flex-wrap의 **shorthand**
- flex-direction 과 flex-wrap에 대한 설정 값을 차례로 작성
- 예) `flex-flow: row nowrap;`

#### justify-content

- main 축 정렬
- flex-start(**기본 값**): 시작 지점부터 차례로 쌓임
- flex-end: **쌓이는 방향이 뒤쪽부터 시작**<br>(순서가 역순이 되는게 아니라 아이템들이 뒤로 몰리는 형식)
- center: 정 중앙
- space-between: **좌우정렬 ( item들 간의 간격 동일 )**<br>(양끝에 아이템 하나씩 그리고 내부 정렬)
- space-around: **균등 좌우 정렬( 내부 요소 여백은 외곽 여백의 2배 )**<br>(아이템의 좌우공백의 너비가 같음)
- space-evenly: **균등 정렬( 내부 요소 여백과 외각 여백 모두 동일)**

#### align-items

- cross: 축 정렬
- stretch (기본 값): 컨테이너를 가득 채움
- flex-start: 위
- flex-end: 아래
- center: 가운데
- baseline: item 내부의 text에 기준선을 맞춤

#### align-self

- 개별 item에 적용하는 속성 <br>(정렬 방식은 align-items와 동일, 속성이 적용되는 대상이 다름)
- auto (기본값)
- flex-start
- flex-end
- center
- baseline
- stretch: 부모 컨테이너에 자동으로 맞춰서 늘어남

#### order

- 작은 숫자일수록 앞(우선 쌓이는 방향)으로 이동
- 기본값: 0
- 음수 지정도 가능

#### flex-grow

- 주축에서 남는 공간(컨텐트 너비를 제외한 공백)을 항목들에게 분배하는 방법
- 각 아이템의 상대적 비율을 정하는 것이 아님
- 기본값: 0
- 음수 불가능

