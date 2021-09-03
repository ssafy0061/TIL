[FLEXBOX FROGGY](https://flexboxfroggy.com/#ko)

flexbox 연습 사이트



CSS에서의 flexbox



```css
#pond {
  display: flex;
  /* 여기에 flexbox 속성과 값 추가 */
}
```



### justify-content

- 이 속성은 요소들을 가로선 상에서 정렬하며 다음의 값을 인자로 받음
  - flex-start: 메인축 left
  - flex-end: 메인축 right
  - center: 가운데 정렬
  - space-between: 양쪽 끝에 배치하고 내부는 동일 간격
  - space-around: 바깥여백의 2배를 내부여백으로, 내부여백은 동일
  - space-evenly: 모든 여백 동일



### align-items

- 다음의 값을 인자로 받아 요소들을 크로스 축 상에서 정렬
  - flex-start: 크로스축 top
  - flex-end: 크로스축 bottom
  - center: 가운데 정렬
  - baseline: 텍스트 기준 정렬
  - stretch(기본값): 요소를 컨테이너에 맞게 늘림



### 수평 수직 가운데 정렬

```css
#pond {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

- 이처럼 수평 수직 같이 쓸 수 있음



### flex-direction

- 다음의 값을 인자로 받아 메인축 정렬 방향을 지정
  - row (기본값): 텍스트 방향과 동일
  - row-reverse: 텍스트 반대방향
  - column: 위에서 아래로
  - column-reverse: 아래에서 위로



### order

- **각 요소**에 order 속성을 적용 가능
- 기본값은 0이며 양수나 음수로 변경가능
- 작은 숫자부터 정렬

```css
#pond {
  display: flex;
}

.red {
  order: -1
}
```



### align-self

- 각 요소에 적용할 수 있는 또 다른 속성
- align-items가 사용하는 값을 인자로 받음
- 값을 지정한 요소에만 적용
  - flex-start: 메인축 left
  - flex-end: 메인축 right
  - center: 가운데 정렬
  - baseline: 텍스트 기준 정렬
  - stretch(기본값): 요소를 컨테이너에 맞게 늘림



### flex-wrap

- 컨테이너를 넘어 갈 경우 다음 줄로 넘김
  - nowrap (기본값): 모든 요소를 한 줄에 정렬
  - wrap: 요소들을 여러 줄에 걸쳐 정렬
  - wrap-reverse: 요소들을 여러 줄에 걸쳐 반대로 정렬



### flex-flow

- 공백문자를 이용하여 두 속성(direction, wrap)의 값들을 인자로 받음

```css
flex-flow: row wrap
```



### align-content

- 여러 줄 사이의 간격을 지정, 다음의 값을 인자로 받음
  - flex-start: 크로스축 top
  - flex-end: 크로스축 bottom
  - center: 가운데 정렬
  - space-between
  - space-around
  - space-evenly
  - stretch(기본값): 요소를 컨테이너에 맞게 늘림
- items는 한 줄, 컨테이너 안에서 어떻게 모든 요소들이 정렬하는지를 지정
- 한 줄만 있는 경우 content는 효과X