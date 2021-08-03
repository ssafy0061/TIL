### 개발환경설정 - Text editor

#### Visual Studio Code

- Html/css 코드 작성을 위한 Visual Studio Code 추천 확장 프로그램
  - Live Server
  - Auto rename tag
  - Highlight Matching Tag

#### Chrome(크롬 개발자 도구)

- 웹 브라우저 크롬에서 제공하는 개발과 관련된 다양한 기능을 제공
- 주요 기능
  - Elements - DOM 탐색 및 CSS 확인 및 변경
    - Styles: 요소에 적용된 CSS확인
    - Computed: 스타일이 계산된 최종 결과
    - Event Listeners: 해당 요소에 적용된 이벤트(JS)

###  

# 웹 표준

각각의 브라우저마다 있는 비표준 기술을 하나로 통일하기 위함

- W3C
  - HTML5
- WHATWG
  - HTML Living Standard(Apple, Google, Microsoft, Mozilla)
- 현재는 WHATWG 중심으로 통합

### 브라우저 표준 점수 확인

[HTML5test](https://html5test.com/)

### Can i use?

[Can i use?, 브라우저에서 사용할 수 있는 기술 확인하기](https://www.caniuse.com/)





# HTML

**Hyper Text Markup Language**

- 웹 페이지를 작성하기 위한(구조를 잡기 위한) 언어
  - 웹 컨텐츠의 의미와 구조를 정의
- 확장자명
  - .html

### Hyper Text

기존의 선형적인 텍스트가 아닌 비선형적으로 이루어진 텍스트

- Hyper
  - 텍스트 등의 정보가 동일 선상에 있는 것이 아니라 다중으로 연결되어 있는 상태
- Hyper Text
  - 참조(하이퍼링크)를 통해 사용자가 한 문서에서 다른 문서로 즉시 접근할 수 있는 텍스트

- Hyper Text가 쓰인 기술들 중 가장 중요한 2가지
  - http
  - html

### Markup

`<h1>` 단순히 큰 글자로 만들뿐만 아니라 '주제'라는 역할도 부여함

즉, 텍스트에 역할을 부여하고 마킹을 하는 것



### Markup Language(마크업 언어)

- 태그(요소, element) 등을 이용하여 문서나 데이터의 구조를 명시하는 언어
- 프로그래밍 언어와는 다르게 단순하게 데이터를 표현하기만 한다.
- 예) HTML, Markdown
- 즉, HTML은 프로그래밍 언어가 아니다
  - 구조화해서 표현만 할 뿐 저장, 조건, 반복을 못함



## HTML 기본구조

```html
<!DOCTYPE html>
<html lang="ko">
<head>
  <meta charest="UTF-8">
  <title>Document</title>
</head>
<body>
    
</body>
</html>
```

- html 요소
  - `<html> </html>` 사이
  - HTML 문서의 **최상위 요소**(태그, element)
  - 문서의 root를 뜻한다.
  - head와 body 부분으로 구분
- head 요소
  - `<head> </head>` 사이
  - 문서 제목, 문자코드(인코딩)와 같이 해당 문서 정보를 담고 있음
  - **브라우저에 나타나지 않음**
  - CSS 선언 혹은 외부 로딩 파일 지정 등을 작성
  - Open Graph Protocol: HTML 문서의 메타 데이터를 통해 문서의 정보를 전달
    - url 공유할 때 사이트의 요약정보를 미리 보여줌
- body 요소
  - 브라우저 화면에 나타나는 정보(실제 내용)

### DOM(Document Object Model) 트리

- DOM은 문서의 구조화된 표현을 제공
  - 각 객체마다 조작, 수정, 삭제 가능
  - **들여쓰기 2spaces** (4spaces도 가능은 하나 안씀)
- 프로그래밍 언어가 DOM구조에 접근할 수 있는 방법 제공
- 문서 구조, 스타일 내용등을 변경 할 수 있게 도움



- DOM은 동일한 문서를 표현하고, 저장하고, 조작하는 방법을 제공
- Web Page의 객체 지향 표현



### 문법

#### 요소(태그, element)

- HTML의 요소는 시작 태그와 종료 태그 그리고 태그 사이에 위치한 내용으로 구성
  - 태그(요소, element)는 컨텐츠(내용)를 감싸는 것으로 그 정보의 성격과 의미를 정의
- 내용이 없는 태그들
  - br, hr, img, inpt, link, meta
- 요소는 중첩(nested)될 수 있음
  - 요소의 중첩을 통해 하나의 문서를 구조화
  - 여는 태그와 닫는 태그의 쌍을 잘 확인해야 함
  - 오류를 반환하는 것이 아닌 그냥 레이아웃이 깨진 상태로 출려되기 때문에 디버깅이 힘듦

#### 속성(attribute)

```html
<a href="https://google.com"></a>
```

- 위에서 `href`는 속성 이름, `https://google.com`은 속성값이다.
- 태그 별로 사용할 수 있는 속성은 다르다
- **등호(=) 앞뒤로 공백X**
- **""(쌍따옴표)만 사용**



- 속성을 통해 태그의 부가적인 정보를 설정할 수 있음
- 요소는 속성을 가질 수 있으며, 경로나 크기와 같은 추가적인 정보를 제공
- 요소의 시작 태그에 작성하며 **보통 이름과 값이 하나의 쌍**으로 존재
- **태그와 상관없이 사용 가능한 속성**(HTML Global Attribute)들도 있음
  - 모든 HTML 요소가 공통으로 사용할 수 있는 속성(몇몇 요소에는 아무 효과 없음)
    - id, class
    - hidden
    - lang
    - style
    - tabindex
    - title

#### 코드 작성 예시

- 항상 처음에는 `<!DOCTYPE html>`로 시작
  - 이 문서는 HTML문서라고 알려주는 역할
- a 태그는 하이퍼링크 만들기
- 주석은 파이썬처럼 `ctrl + /`



### 시맨틱 태그

- 태그 `<div> </div>`는 의미를 가진 태그가 적절하지 않을 때 사용
  - CSS로 스타일을 지정할 때까지 내용이나 레이아웃에 영향X
  - 즉, 구조를 잡기 위해 사용
  - 남용하는 경우 가독성 떨어짐
  - 검색엔진, 브라우저에 명확한 의미 전달X(접근성)
- div 쓰기보다는 **다음의 대표 태그들로 의미를 표현하는 것이 좋다**
  - header: 문서 전체나 섹션의 헤더(머릿말 부분)
  - nav: 내비게이션
  - aside: 사이드에 위치한 공간, 메인 콘텐츠와 관련성이 적은 콘텐츠
  - section: 문서의 일반적인 구분, 컨텐츠의 그룹을 표현
  - article: 문서, 페이지, 사이트 안에서 독립적으로 구분되는 영역
  - footer: 문서 전체나 섹션의 푸터(마지막 부분)

정리

- 개발자 및 사용자 뿐만 아니라 검색엔진 등의 의미있는 정보의 그룹을 태그로 표현
- 단순히 구역을 나누는 것 뿐만 아니라 '의미'를 가지는 태그들을 활용하기 위한 노력
- Non semantic 요소는 div, span 등이 있으며
- h1, table 태그들도 시맨틱 태그로 볼 수 있음
- 요소의 의미가 명확해지기 때문에 코드의 가독성을 높이고 유지보수를 쉽게 함
- 검색엔진최적화(SEO)를 위해 메타태그, 시맨틱 태그 등을 통한 마크업을 효과적으로 할 필요가 있다.

#### 시맨틱 웹

- 웹 상에 존재하는 수많은 웹 페이지들에 메타데이터를 부여하여,
- 기존의 단순한 데이터의 집합이었던 웹페이지를 '의미'와 '관련성'을 가지는 거대한 데이터베이스로 구축하고자 하는 발상



## HTML 문서 구조화

##### 인라인/ 블록 요소

- 블록은 한 칸 다 차지
- 인라인은 자기 데이터만 차지
- CSS에서 자세히 다룸

### 그룹 컨텐츠

- `<p>` 문단
- `<hr>` 헤드라인
- `<ol>`, `<ul>`  순서가 있는/없는 목록(ordered list / unordered list)
- `<pre>` 주석 `<blockquote>` 인용문
- `<div>`

### 텍스트 관련 요소

- `<a>` 하이퍼 텍스트
- `<b>` 문서 표현상 굵게
  - `<strong>`  텍스트 굵게 + 의미 강조
  - 스크린 리더가 strong은 강하게 읽어줌(`<b>` 는 일반 문장처럼 읽음)
  - 즉, 웹 접근성을 높여줌 [네이버 nuli(널리) 참고](https://nuli.navercorp.com/)
- `<i>` 이탤릭체
  - `<em>` 이탤릭체 + 의미 강조
- `<span>` 텍스트만큼 차지
- `<br>` 개행(다음 단락으로)
- `<img>` 이미지 첨부
- 기타 등등



### table 요소

행과 열로 이루어진 표

(최근에 사용 잘 안함)

- `<tr>, <td>, <th>` 

  - table row 표 내부의 행
  - table heading 행 내부의 제목 셀
  - table data 행 내부의 일반 셀

  ```html
  <tabel>
    <tr>
      <th>1행 제목1</th>
      <th>제목2</th>
      <th>제목3</th>  
    </tr>
    <tr>
      <td>2행 내용1</td>
      <td>내용2</td>
      <td>내용3</td>  
    </tr>    
    <tr>
      <td>3행 내용1</td>
      <td>내용2</td>
      <td>내용3</td>  
    </tr>    
  </tabel>
  ```

- `<thead>, <tbody>, <tfoot>, <caption>`
- 셀 병합 속성: colspan, rowspan
- scope 속성
- `<col>, <colgroup>`



### form	(중요)

- `<form>`은 로그인 창, 검색창 등 입력한 값을 서버로 보낼 때 사용
- 기본 속성
  - action: 어디로 보낼지
  - method: http method 중에 어떤 것을 선택할 지

#### input

- form 안에서 이용하면 사용자의 입력값을 받아 form이 서버로 보냄
- 다양한 타입을 가지는 입력 데이터 필드
- `<lable>` 서식 입력 요소의 캡션
- `<input>` 공통 속성
  - name, placholder
  - required
  - autofocus
- `<input>` 요소의 동작은 type에 따라 달라지므로 내용 숙지 필요
  - [MDN 사이트 참고](https://developer.mozilla.org/ko/docs/Web/HTML/Element/Input)

