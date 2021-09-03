## Bootstrap

### 세계적으로 유명한 프론트앤드 오픈소스

The most popular HTML, CSS and JS library in the world

[공식문서](https://getbootstrap.com/docs/5.0/getting-started/introduction/)

- 트위터에서 시작된 오픈 소스 프론트엔드 라이브러리
- 별도의 디자인을 할 시간이 크게 줄어들고, <br>여러 웹 브라우저를 지원하기 위한 **크로스 브라우징**에 불필요한 시간을 사용하지 않도록 함
- one source multi use
  - 반응형 웹 디자인(웹을 만들면 모바일에서도 잘 보여줌)
- 특징 요약
  - quickly design
  - responsive movie-first sites
  - responsive grid system
  - prebuilt components
- Bootstrap으로 만든 사이트: 넷플릭스
  - 크롬 확장프로그램 wappalyzer를 설치하면 웹사이트별 개발환경 확인 가능



### 사용방식1

- [설치(다운로드)](https://getbootstrap.com/docs/5.0/getting-started/download/)
  - 압출 풀고 js 폴더에서는 bootstrap.bundle.js 파일을,
  - css폴더에서는 bootstrap.css 파일을 html문서가 있는 폴더에 가져오기

```css
<head>
  <link rel="stylesheet" href="bootstrap.css">
</head>
<body>

/* body 끝나는곳 바로 위에 아래 입력 */
  <script src="bootstrap.bundle.js"></script>
</body>
```



첨부파일 확인

css reset/normalize

- 브라우저마다 기본 스타일(user agent stylesheet)이 다 다름
- 웹 개발할 때 최대한 동일하게 맞춰주는 초기화 작업 필요
  - Normalize CSS
  - Reset CSS

Normalize CSS

gentle solution(표준 낮은 것 기준으로 바꿈)

- W3C의 표준을 기준으로 브라우저 중 하나가 불일치 한다면 차이가 있는 브라우저를 수정
- bootstrap이 하는 초기화 방식

Reset CSS

aggressive solution

- 브라우저의 기본 스타일이 전혀 필요 없다는 방식으로 접근
- 브라우저의 user agent와 함께 제공되는 모든 스타일을 재설정
- 너무나 많은 선택자가 엉켜있고, 불필요한



### 사용방식2  CDN

[bootstrap.com/docs에서](https://getbootstrap.com/docs/5.0/getting-started/introduction/) CSS는 head에, JS는 `</body>`위에 링크 붙여넣기

66 jsDeliver 사이트도 있음

#### CDN

- Content Delivery(Distribution) Network
- 컨텐츠(CSS, JS, Image, Text 등)을 효율적으로 전달하기 위해<br>서버와 사용자 사이의 물리적 거리를 줄여 컨텐츠 로드 지연을 최소화
- 분산 된 서버로 이루어진 플랫폼
  - 전 세계 사용자들이 로딩 시간을 늦추지 않고 동일한 품질의 컨텐츠를 사용할 수 있음
- 장점
  - 사용자와 가까운 서버를 통해 빠르게 전달 가능
  - 외부 서버를 활용함으로써 본인 서버의 부하가 적어짐

### spacing

- .mt-1

  ```css
  .mt-1 {
    margin-top: 0.25rem !important;
  }
  ```

  - 16 * 0.25 = 4px

| class name | rem  | px   |
| ---------- | ---- | ---- |
| m-1        | 0.25 | 4    |
| m-2        | 0.5  | 8    |
| m-3        | 1    | 16   |
| m-4        | 1.5  | 24   |
| m-5        | 3    | 48   |

- .mx-0

  ```css
  .mx-0 {
    margin-right: 0 !important;
    margin-left: 0 !important;
  }
  ```

  - x축 즉, 좌우
  - y는 상하

- .mx-auto는 수평 중앙정렬

- .py-0은 padding 상하

|  m   | margin  |  t   | top         |  0   | 0rem    | 0px  |
| :--: | :------ | :--: | :---------- | :--: | :------ | :--- |
|  p   | padding |  b   | bottom      |  1   | 0.25rem | 4px  |
|      |         |  s   | left        |  2   | 0.5 rem | 8px  |
|      |         |  e   | right       |  3   | 1 rem   | 16px |
|      |         |  x   | left, right |  4   | 1.5 rem | 24px |
|      |         |  y   | top, bottom |  5   | 3 rem   | 48px |

### color

- color도 적용할 수 있음
- bg-primary
- bg-secondary
- bg-dark
- bg-light
- bg-whilte

### Flexbox in Bootstrap

예시

```html
<div class="d-flex justify-content-strat">...</div>
<div class="d-flex align-items-strat">...</div>
<div class="d-flex">
    <div class="align-self-start">Aligned flex item</div>
</div>
```

- .d-flex
- flex도 클래스로 구현돼 있음

### Responsive Web Design

- 다양한 화면 크기를 가진 디바이스들이 등장함에 따라 responsive web design 개념이 등장
- 반응형 웹은 별도의 **기술이름이 아닌 웹 디자인에 대한 접근 방식**,<br>반응형 레이아웃 작성에 도움이 되는 사례들의 모음 등을 기술하는 데 사용되는 용어
- 예시
  - Media Queries, Flexbox, Bootstrap Grid System, The viewport meta tag



## Bootstrap Grid System

- 특징
  - flexbox grid
  - 12 column
  - 6 default responsive tiers: 반응형 6개

### Grid system

[공식문서](https://getbootstrap.com/docs/5.0/layout/grid/)

- Bootstap Grid system은 flexbox로 제작됨
- `container`, `rows`, `column`으로 컨텐츠를 배치하고 정렬
  - 컨테이너 안에 행, 그리고 행안에 12개의 열<br>(flexbox은 컨테이너 안에 아이템)
- 반드시 기억해야 할 2가지
  - 12개의 column
    - 약수가 많아서 12개로 정함
  - 6개의 grid breakpoints

```css
<body>
  <div class="container">
    <h2 class="text-center">column class - 1</h2>
    <div class="row">
      <div class="box col-4">1</div>
      <div class="box col-4">2</div>
      <div class="box col-4">3</div>
    </div>
```

- class="container"
  - 컨테이너
- class="row"
- class="col"
  - class="col-4": 12개 열 중 4열 차지
  - 4, 6, 3으로 총 13개를 하면<br>12를 넘게 되는 3은 다음 줄에 나옴



```css
    <h2 class="text-center">column class - 2</h2>
    <div class="row">
      <div class="box col">1</div>
      <div class="box col">2</div>
      <div class="w-100"></div>
      <div class="box col">3</div>
      <div class="box col">4</div>
    </div>
```

- 중간에 `<div class="w-100"></div>`를 넣으면<br>첫 행에 1 2 두번째 행에 3 4가 됨





- row

  - columns의 wrapper

- gutters

  - grid시스템에서 반응적으로 공간을 확보하고 컨텐츠를 정렬하는 데 사용되는 column 사이의 padding 값

  ```css
  class="row gx-5"
  
  /* padding 값 0 */
  class="row g-0"
  ```

- col, col-*
  - column class는 row 당 가능한 12개 중 사용하려는 columns 수를 나타냄
  - column 너비는 백분율로 설정 되므로 항상 부모 요소를 기준으로 유동적으로 크기가 조정됨
  - grid layout에서 내용은 반드시 columns 안에 있어야 하며<br>오직 columns만 row의 바로 하위 자식일 수 있음

### Grid breakpoints

- 다양한 디바이스에서 적용하기 위해<br>특정px(픽셀) 조건에 대한 지점(**6개**)을 정해 두었는데<br>이를 breakpoints라고 함( [참고](https://getbootstrap.com/docs/5.0/layout/grid/#grid-options) )

  |              | xs     | sm       | md       | lg       | xl       | xxl       |
  | ------------ | ------ | -------- | -------- | -------- | -------- | --------- |
  |              | <576px | >=576px  | >=768px  | >=992px  | >=1200px | >=1400px  |
  | Class prefix | .col-  | .col-sm- | .col-md- | .col-lg- | .col-xl- | .col-xxl- |

  ```css
      <div class="row">
        <div class="box col-2 col-sm-8">1</div>
        <div class="box col-8 col-sm-2">2</div>
        <div class="box col-2 col-sm-2">3</div>
  ```

  

- bootstrap은 대부분의 크기를 위해 em 또는 rem을 사용하지만<br>grid breakpoint에서는 px 사용

  - viewport 너비가 픽셀 단위이고 글꼴 크기에 따라 변하지 않기 때문



### nesting (중첩)

- row > col-* > row > col-*의 방식으로 중첩 사용 가능

```css
    <div class="row">
      <div class="box col-6">
        <div class="row">
          <div class="box col-3">1</div>
          <div class="box col-3">2</div>
          <div class="box col-3">3</div>
          <div class="box col-3">4</div>
        </div>
      </div>
      <div class="box col-6">1</div>
      <div class="box col-6">2</div>
      <div class="box col-6">3</div>
    </div>
```

- nesting 된 row는 12칸중 6칸 차지
  - 1, 2, 3, 4는 6칸을 12칸으로 나누어 그 12칸 중에 설정한 3칸씩 차지
- 즉, nesting된 요소는 12칸으로 나누어 계산

### offset

- 지정한 만큼의 column 공간을 무시하고 다음 공간부터 컨텐츠를 적용

  ```css
      <div class="row">
        <div class="box col-md-4 offset-4">.col-md-4 .offset-4</div>
        <div class="box col-md-4 offset-md-4 offset-lg-2">.col-md-4 .offset-md-4 .offset-lg-2</div>
      </div>
  ```

  - breakpoint 적용 가능



## 마무리

- position
  - 문서 상에 요소를 배치하는 방법을 지정
- float
  - 한 요소(element)가 정상 흐름(normal flow)으로부터 빠져 <br>텍스트 및 인라인(inline) 요소가 그 주위를 감싸<br> 요소의 좌, 우측을 따라 배치되어야 함을 지정
- flexbox
  - 아이템 간 공간 배분과 강력한 정렬 기능을 제공하기 위한 1차원 레이아웃 모델
- bootstrap gird system
  - 강력한 모바일 우선 Flexbox 그리드를 사용하여 모든 모양과 크기의 레이아웃을 구축<br>(12개의 열 시스템, 6개의 반응형 계측 덕분에 가능)



- 각각의 기술은 저마다 용도가 있고, 장단점이 있으며<br>어떤 기술도 독립적인 용도를 갖추도록 설계되지는 않았다.
- 특정 상황에 어떤 기술이 가장 적합한 도구가 될 것인지<br>파악하는 데에는 많은 경험이 뒷받침되어야 한다.