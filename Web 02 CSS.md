# CSS

Cascading Style Sheets

- 스타일, 레이아웃 등을 통해 문서(HTML)를 표시하는 방법을 지정하는 언어

### 구문

```css
h1 {
  color: blue;
  font-size: 15px;
}
```

- h1
  - 선택자(Selector)

- color: blue
  - 선언(Declaration)
- color, font-size
  - 속성(Property)
- blue, 15px
  - 값(Value)
- CSS 구문은 선택자와 함께 열림
- 선택자를 통해 스타일을 지정할 HTML 요소를 선택
- 중괄호 안에서는 속성과 값, 하나의 쌍으로 이루어진 선언을 진행
- 각 쌍은 선택한 요소의 **속성**, 속성에 부여할 **값**을 의미
  - 속성(Property): 어떤 스타일 기능을 변경할지 결정
  - 값(Value): 어떻게 스타일 기능을 변경할지 결정

### 정의 방법 (3가지)

- 인라인(inline)

  ```css
  <h1 style="color: blue; font-size: 100px;">Hello</h1>
  ```

  - 해당 태그에 직접 style 속성을 활용

- 내부 참조(embedding) - `<style>`

  ```css
  <!DOCTYPE html>
  <html>
  <head>
    <style>
      h1 {
        color: blue;
        font-size: 100px;
      }
    </style>
  </head>
  <body>
      
  </body>
  </html>
  ```

  - head 태그 내에 `<style>  </style>` 지정

- 외부 참조(link file) - 분리된 CSS 파일

  ```css
  <head>
    <link rel="stylesheet" href="mystyle.css">
  </head>
  ```

  - 외부 CSS 파일을 `<head>` 내 `<link>`를 통해 불러오기

  ```css
  h1 {
    color: blue;
    font-size: 100px;
  }
  ```

  - mystyle.css

- 내부참조는 같은 내용 반복될 수 있음

- 3가지 방법 모두 각자 유리한 상황이 있음



## 선택자 Selector

- HTML 문서에서 특정한 요소를 선택하여 스타일링 하기 위해서<br>반드시 선택자라는 개념이 필요

- 기본 선택자

  - 전체 선택자, 요소 선택자
  - class 선택자, id 선택자, 속성 선택자

- 결합자(Combinators)

  - 자손 결합자, 자식 결합자
  - 일반 형제 결합자, 인접 형제 결합자

- 의사 클래스/요소(pseudo class)  (참고만 하기)

  - 링크, 동적 의사 클래스
  - 구조적 의사클래스, 기타 의사 클래스, 의사 엘리먼트, 속성 선택자

- ```css
  #id선택자 > div.sub > ul > li
  ```

  - 하나하나 모두 선택자

정리

- 요소 선택자
  - HTML 태그를 직접 선택
- 클래스(class) 선택자
  - 마침표(.)문자로 시작하며,
  - 해당 클래스가 적용된 모든 항목을 선택
- 아이디(id) 선택자
  - `#` 문자로 시작하며
  - 해당 아이디가 적용된 모든 항목을 선택
  - 일반적으로 하나의 문서에 1번만 사용
  - 여러 번 사용해도 동작하지만, 단일 id를 사용하는 것을 권장

### 적용 우선순위(cascading order)

아래와 같이 3개의 그룹을 지어볼 수 있다.

- 중요도(Importance)  (영향이 크기 때문에 거의 안씀)
  - !important
- 우선순위(Specificity)
  - 인라인
  - id 선택자
  - class 선택자  (일반적으로 class 만 사용)
  - 요소 선택자

- 소스 순서

#### 예시

```css
<p class="blue green">1</p>
<p class="green blue">2</P>
```

여러 클래스를 정한 경우

`<style>` 에서 순서가 blue, green 순인 경우

1, 2 둘 다 green (**마지막 기준**)



### 상속

- 상속을 통해 부모 요소의 속성을 (모두 X) 일부 자식에게 상속 가능
  - 속성(property) 중에는 상속이 되는 것과 되지 않는 것들이 있다.
  - **상속 가능**
    - Text 관련 요소(font, color, text-align), opacity, visibility 등
  - **상속 불가능**
    - Box model 관련 요소(width, height, margin, padding, border, box-sizing, display)
    - Position 관련 요소(position, top/right/bottom/left, z-index) 등

```css
<style>
  p {
    /* 상속 가능 */
    color: red;
    /* 상속 불가능 */ 
    border: 1px solid black;
  }
  span {
    border: 1px solid blue;
  }
</style>

<p>1<span>2</span>3</p>
```

- color는 상속
- border는 상속안됨, 2는 파란 테두리



### 결합자 (Combinators)

- 자손 결합자( **A B** )

  - selectorA 하위의 모든 selectorB 요소

- 자식 결합자( **A > B** )

  - selectorA 바로 아래의 selectorB 요소

- 일반 형제 결합자( **A ~ B** )

  - selectorA의 형제 요소 중 뒤에 위치하는 selectorB 요소를 **모두** 선택

- 인접 형제 결합자( **A + B**)

  - selectorA의 형제 요소 중 바로 뒤에 위치하는 selectorB 요소를 선택

  - p + p 인경우 다음은 2, 3, 4 모두 선택됨 (3은 2다음 p이므로..)

  - ```css
    <p>1</p>
    <p>2</p>
    <p>3</p>
    <p>4</p>
    ```



## CSS 단위

### 크기 단위

- px(픽셀)
  - 모니터 해상도의 한 화소인 '픽셀'을 기준
  - 픽셀의 크기는 변하지 않기 때문에 고정적인 단위
- %
  - 백분율 단위
  - 가변적인 레이아웃에서 자주 사용
- em
  - (**바로 위**, 부모 요소에 대한) 상속의 영향을 받음
  - 배수 단위, 요소에 지정된 사이즈에 상대적인 사이즈를 가짐
  - 부모 10px, 2em인 경우 20px
- **rem**
  - (바로 위, 부모 요소에 대한) 상속의 영향을 받지 않음
  - 최상위 요소(html)의 사이즈(**16px**)를 기준으로 배수 단위를 가짐.

```css
<style>
  .em {
    font-size: 1.5em; 
 }
  .rem {
    font-size: 1.5rem; 
 }
</style>

<ul class="em">
  <li class="em">1</li>
  <li class="rem">2</li>
  <li>3</li>
</ul>
```

- 1은 36px, 2는 24px, 3은 24px
- 부모 요소인 `<ul>`에 24px 됨



- **viewport**
  - 웹 페이지를 방문한 유저에게 바로 보이게 되는 웹 컨텐츠의 영역
  - 주로 스마트폰이나 태블릿 디바이스의 화면을 일컫는 용어로 사용됨
  - 글자 그대로 디바이스의 viewport를 기준으로 상대적인 사이즈가 결정됨
  - vw, vh, vmin, vmax



### 색상 단위

- 색상 키워드
  - 대소문자 구분X
  - red, blue, black 과 같은 특정 색을 직접 글자로 나타냄
  - `p { color: black; }`
- RGB 색상
  - 16진수 표기법 혹은 함수형 표기법을 사용해서 특정 색을 표현하는 방식
  - '#' + 16진수 표기법 `p { color: #000;}` `p { color: #000000; }`
  - rgb() 함수형 표기법 `p { color: rgb(0, 0, 0); }`
- HSL 색상
  - 색상, 채도, 명도를 통해 특정 색을 표현하는 방식
  - `p { color: hsl(120, 100%, 0); }`
- a는 alpha(투명도)가 추가된것
  - `p { color: rgba(0, 0, 0, 0.5); }`
  - `p { color: hsla(120, 100%, 0, 0.5) }`

### 문서 표현

- 텍스트
  - 변형 서체(`<b>, <i> vs <strong>, <em>`)
- 컬러(color), 배경(background-image, background-color)
- 목록 꾸미기



