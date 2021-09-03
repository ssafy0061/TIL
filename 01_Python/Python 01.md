# 특징 & 환경

### Python 특징

- 인터프리터(Interpreter)
  - 소스 코드를 컴파일X, 한 줄씩 읽어서 바로 실행
  - 컴파일 언어(C언어 등)에 비해 느리지만 빌드과정 없이 바로 실행 가능
- 객체 지향 프로그래밍(OOP, Object Oriented Programming)
  - 파이썬은 모두 객체
- 동적 타이핑(Dynamic Typing)
  - 변수에 별도의 타입 지정 필요없음



### 개발환경

- 대화형 환경
  - 기본 Interpreter, Jupyter Notebook
- 스크립트 실행
  - .py 파일을 작성하고 IDE 또는 Text editor 활용



### Python Interpreter / IDLE

- 인터프리터 = 대화형

  - 프롬프트(>>>)에 코드 작성하면 실행됨
  - 여러 줄의 코드는 보조 프롬프트(...)가 사용됨

- Python  설치만으로 활용 가능하나

  디버깅 및 코드편집, 반복 실행이 어려움



### Python Jupyter Lab

- 웹 브라우저 환경에서 코드를 작성할 수 있는 오픈소스

  - Syntax Highlighting, Indentation, Tab completion 등 편의 기능 제공
  - 코드 실행하고 결과를 바로 확인 가능
  - HTML, LaTeX, PNG, SVG을 바탕으로 다양한 표현 가능
  - Markdown 기반 문서 작성가능

- 데이터분석/머신러닝/딥러닝 시 많이 활용가능하며

  Google colab 등 유사 서비스 많이 존재

- 처음에는 **Jupyter Notebook** 활용



### Python 스크립트 실행

- **IDE**(Pycharm 파이참 등), **Text editor**(Visual Studio code 등) 등에서<br>작성한 파이썬 스크립트 파일을 직접 실행







# 기초

### 코드 스타일 가이드

가독성 좋은 글쓰기처럼 문법은 아니지만 지키면 보기좋음

**PEP8** - 파이썬에서 제안하는 스타일 가이드<br>https://www.python.org/dev/peps/pep-0008/

Google Style guide처럼 기업, 오픈소스 등에서 사용되는 스타일 가이드도 있음<br>https://google.github.io/styleguide/pyguide.html

- 일관적인 코드 작성스타일
  - 들여쓰기, 따옴표, 띄어쓰기 등



### 주석(Comment) ###

- 여러 줄 주석(#) : 범위 블록 지정 후 ctrl + /
  - """ 또는 ''': 여러 줄 주석보다는 docstring(코드 설명)으로 씀
- docstring: 특수한 형태의 주석
  - 함수, 클래스, 모듈 등의 설명서(가이드라인)



### 코드라인

- 코드는 1줄에 1문장(statement)이 원칙

- ##### 문장: 실행가능한 최소한의 코드 단위

  - 세미콜론(;) 사용X
  - 세미콜론으로 한 줄 표기가 가능하나 스타일가이드에서 권장하지 않음





# 변수와 식별자

### 변수

```
a = 10
```

할당연산자(**=**)를 통해 **값**을 **할당**(assignment)

- type()<br>변수에 할당된 값의 타입(type)을 확인

```
x = aaple
type(x)
```

- id()<br>변수에 할당된 값(객체)의 고유한 아이덴티티(identity) 값을 확인<br>(파이썬 내부 메모리 주소)

#### 할당 연산자(=)

- 같은 값을 동시에 할당: `x = y = 1`
- 다른 값을 동시에 할당: `x, y = 1, 2`

* **오류**
  * `x, y = 1` 	TypeError: cannot unpack non-iterable int object
  * `x, y = 1, 2, 3 `    ValueError: too many values to unpack (expected 2)

#### 값 swap

x, y 값을 서로 바꾸기

```python
x, y = 10, 20

y, x = x, y
```





### 식별자(identifiers)

변수, 함수, 모듈, 클래스 등을 식별하는 데 사용하는 이름(name)

#### 규칙

- 영문 알파벳, 언더스코어(_), 숫자로 구성
- 첫 글자에 숫자X
- 길이 제한없음, 대소문자 구별
- 다음의 키워드(keywords)는 예약어(reserved words)로 사용X

```python
['False', 'None', 'True', '__peg_parser__', 'and', 'as', 'assert', 'async', 'await', 'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
```

- 키워드 확인 방법

```
import keyword
print(keyword.kwlist)
```

또는

```
from keyword import kwlist
print(kwlist)
```

- 내장함수나 모듈 등의 이름 사용X

  ```python
  print = 'hi'
  print(5)
  ```

  TypeError: 'str' object is not callable

  새로운 값을 할당하면 내장함수 print가 아닌 변수 print를 먼저 인식함

  (문자('hi')를 할당했으므로 str object)

  `del print` 로 원래대로 돌아감

  

# 데이터 타입

- 숫자(Number)
  - **int**  (정수, integer)
  - **float**  (부동소수점, 실수, floating point number)
  - **complex**  (복소수, complex number)
- 문자열(String)
  - **str**

- 참/ 거짓 (Boolean, 불리언)
  - **bool**
- None
  - **NoneType**



### int

- 모든 정수 `<class 'int'>`
- 매우 큰 수를 나타낼 때 오버플로X
  - 오버플로(overflow): 데이터 타입별로 사용할 수 있는 메모리 크기를 넘어서는 상황
  - 임의 정밀도 산술: 가용 메모리를 활용하여 모든 수 표현 가능

#### 진수표현

- 2진수: 0b  (`0b10` = 2)
- 8진수: 0o  (`0o30` = 24)
- 16진수: 0x  (`0x10` = 16)



### float

- 정수가 아닌 모든 실수  `<class 'float'>`

- 부동소수점

  - 컴퓨터는 2진수(비트)로 숫자를 표현하기 때문에 <br>floating point rounding error 발생

  - 1e-1 = 0.1

#### floating point rounding error

- 부동소수점에서 실수 연산 과정에서 발생가능<br>즉, 정수가 아닌 **실수의 값을 비교하는 경우 주의**

- 실수는 무한하기 때문에 2진수 표현에 한계가 있음<br>그래서 근삿값으로 표현하고 값의 차이가 작으면 같다고 봄

  ```python
  print(3.14 - 3.02 == 0.12)
  False
  print(3.14 - 3.02)
  0.1200000000000001
  ```

- 매우 작은 수보다 작은지를 확인하거나 math 모듈 활용

  - ```python
    abs(a - b) <= 1e-10
    ```

  - ```python
    import math
    math.isclose(a, b)
    ```



### complex

- `<class 'complex'>`

- 허수부를 j로 표현 (`3+4j`)

- 실수부, 허수부 확인(float 형태로 반환)

```python
a = 3 + 4j
print(a.real)
3.0
print(a.imag)
4.0
```



### String 문자열

- 모든 문자는 str 타입 `<class 'str'>`

- 작은 따옴표(', apostrophe = single quote 싱글 코트)나 큰 따옴표('', double quotes)로 표기

  - 문자열은 한 종류의 따옴표만 활용

  - PEP8은 소스코드 내에서 하나의 문장부호 권장

  - ```python
    print('say "hello"')
    say "hello"
    print("say 'hello'")
    say 'hello'
    # 이스케이프 시퀀스:  \'는 ', \"는 "를 문자열 내에서 표시
    print('say \'hello\'')
    say 'hello'
    ```



#### 이스케이프 시퀀스(escape sequence)

- 문자열 내에서 특정 문자나 조작을 위해 역슬래시(\\)를 활용

| 예약문자 | 내용(의미)                                                 |
| :------- | ---------------------------------------------------------- |
| \n       | 줄 바꿈                                                    |
| \t       | 탭                                                         |
| \r       | 캐리지 리턴(CR, Carrige Return)<br>: 같은 줄(행) 맨 앞으로 |
| \0       | 널(Null)                                                   |
| \\\\     | \\                                                         |
| \\'      | '                                                          |
| \\"      | "                                                          |



#### String Interpolation

변수를 활용하여 문자열 만들기

##### %-formatting 퍼센트 포메팅

```python
a = 'hello'
print('say %s' % a)
say hello
```

| 기호 | 타입         |
| ---- | ------------ |
| %s   | type         |
| %f   | 실수         |
| %d   | 정수(10진수) |
| %o   | 정수(8진수)  |
| %x   | 정수(16진수) |

- 16진수는 1~9 그리고 A~F(6개)로 이루어짐

```python
num = 11
print('%d, %o, %x' % (num, num, num))
11, 13, b

print('%f, %.2f' % (num, num))
11.000000, 11.00

print(type('%s' % num))
<class 'str'>
```

​	

##### str.format() 스트링 포멧

```python
num = 10
wrd = '포멧'
print('스트링 {}, 결과는 {}개'.format(wrd, num))
스트링 포멧, 결과는 10개
print('스트링 {0}, 결과는 {1}개'.format(wrd, num))
스트링 포멧, 결과는 10개
print('스트링 {1}, 결과는 {0}개'.format(wrd, num))
스트링 10, 결과는 포멧개

print('{number}a{number2}'.format(number=num, number2=2))
10a2
print('{0}a{number2}'.format(num, number2=2))
10a2
# 위치인자 다음에 키워드인자가 와야함
print('{number1}a{1}'.format(number1=num, 2))
SyntaxError: positional argument follows keyword argument

#문자열로 변환(defalult)
print(type('{}'.format(num)))
print(type('{!s}'.format(num)))
<class 'str'>

#소수점 두자리
print('{:.2f}'.format(num))
10.00

#공백에 문자넣기, 정렬, 폭지정
print('{:*<10}a'.format(num))
10********a
print('{:@>10}a'.format(num))
@@@@@@@@10a
print('{:^10}a'.format(num)) # 중앙정렬
    10    a
```



##### f-strings  f 스트링 (formatted string literals)

- python 3.6 이상

```python
num = 10.123
print(f'{num}')
10.123
 
print(f'{num:.3}')
10.1

# 연산 가능
print(f'{num-0.123}')
10.0
```



### 참/거짓 Boolean

Boolean 불리언, bool 부울

- True / False 값을 가지면 `<class 'bool'>` 

- 비교/논리 연산에 이용

- 다음은 모두 False로 변환

  `0, 0.0, (), [], {}, '', None` 



### None

`<class 'NoneType'>`

- 값이 없음을 표현

- `a = None` 처럼 변수에 할당가능

  

  





# 타입변환

### 자료형 변환/ 타입 변환(Type conversion, Typecasting)

- 데이터 타입은 서로 변환 가능
  - 암시적 타입 변환(Implicit): 파이썬 내부
  - 명시적 타입 변환(Explicit): 사용자가 특정 함수를 활용하여 직접 변환



#### 암시적 타입변환

- bool (True는 1)
  - `True + 3` = 4
- Numbers (int, float, complex)
  - `3 + 5.0` = 8.0
  - `3 + 4j + 5` = (8 + 4j)



#### 명시적 타입변환

- str, float => **int**
- str, int => **float**

(단, str는 형식이 맞는 경우 int, float로 변환가능)

- int, float, list, tuple, dict => **str**





# 연산자

### 산술 연산자

기본적인 사칙연산 및 수식 계산

| 연산자 | 내용     |    타입    |
| :----: | -------- | :--------: |
|   +    | 더하기   | int, float |
|   -    | 빼기     |     ''     |
|   *    | 곱하기   |     ''     |
|   /    | 나누기   |     ''     |
|   //   | 몫       |     ''     |
|   %    | 나머지   |     ''     |
|   **   | 거듭제곱 |     ''     |

```python
print(4/2) # 나눈 결과는 소수
2.0
print(5/2)
2.5
print(int(5/2)) # 반올림X
2
print(divmod(5, 2)) # 몫과 나머지를 한번에
(2, 1)
a, b = divmod(5, 2)
print(a, b)
2 1
```



### 비교 연산자

값을 비교하여 True/ False 값을 반환함

| 연산자 | 내용                                      |              타임              |
| :----: | ----------------------------------------- | :----------------------------: |
|   <    | 미만                                      | dict, range를 제외한 모든 타입 |
|   <=   | 이하                                      |               ''               |
|   >    | 초과                                      |               ''               |
|   >=   | 이상                                      |               ''               |
|   ==   | 같음                                      |           모든 타입            |
|   !=   | 같지 않음                                 |               ''               |
|   is   | 객체 아이덴티티(OOP) (동일 변수인지 여부) |               ''               |
| is not | 객체 아이덴티티가 아닌 경우               |               ''               |

- is 와 is not은 메모리 주소를 비교( 값 비교X )

- 특정 변수가 비어있는지 확인하기 위해서<br>`X == None` 보다는 `X is None` 사용 권장



### 논리 연산자

| 연산자  | 내용                     | 타입 |
| ------- | ------------------------ | :--: |
| A and B | A와 B 모두 True면 True   | bool |
| A or B  | A와 B 모두 False면 False |  ''  |
| Not     | True, False를 반대로     |  ''  |

```python
print(not 'hi')
False  
# ''는 False, 값이 있으면 True,  즉, not True가 되므로 False
```

- 일반적으로 비교연산자와 함께 사용됨
- 두 개의 표현식 사이에서 논리연산자 사용됨



#### 단축평가

결과가 확실한 경우 두 번째 값은 확인X

```python
print(3 and 5)
print(3 and 0)
print(0 and 3) # 첫번째 값이 False이므로 첫번째 값 반환
print(0 and 0) # 첫번째 값이 False이므로 첫번째 값 반환
5
0
0
0

print(5 or 3) # 첫번째 값이 True이므로 첫번째 값 반환
print(3 or 0) # 첫번째 값이 True이므로 첫번째 값 반환
print(0 or 3)
print(0 or 0) # 두번째 0
5
3
3
0
```



### 복합 연산자

연산과 대입이 함께 이뤄짐

- 반복문으로 개수 카운트 하기

  ```python
  cnt = 0
  while cnt <3:
      print(cnt)
      cnt += 1
  
  0
  1
  2
  ```

  

  

### 기타

#### Concatenation 연속, 연결

+는 숫자가 아닌 자료형(str, list, tuple)에서도 사용가능

```python
print('a' + 'b')
'ab'
# 리스트 합치기
print([1] + [2]) 
[1, 2]
# 리스트에 추가
a = []
for i in range(4):
    a += [1]
print(a)
[1, 1, 1, 1]

# 튜플 합치기
print((1,) + (2,)) # 하나의 항목으로 구성된 튜플은 생성시 값 뒤에 콤마(,) 필요
(1, 2)
```

#### repetition 반복

*는 자료형(str, list, tuple)에서 사용 가능

```python
print('a' * a)
aaa
print((1, 2, 3) * 2)
(1, 2, 3, 1, 2, 3)
print([0] * 2)
[0, 0]
```



#### Containment Test

특정 요소가 속해 있는지 여부를 확인

```python
print('a' in 'aaple')
True
```



#### Identity

is 연산자를 통해 동일한 객체(object)인지 확인 가능함

```python
a = 3
b = 3
print(a is b)
True
print(id(a), id(b))
2244148750704 2244148750704
```

- 특정 변수가 비어있는지 확인하기 위해서<br>`X == None` 보다는 `X is None` 사용 권장



#### Indexing / Slicing

[]를 통해 값에 접근하고, [:]를 통해 슬라이싱 함

```python
print('aaple'[0])
a
print('aaple'[1:3])
ap
```



### 연산자 우선 순위

- ()
- Slicing
- Indexing
- **
- 단항 연산자(+, -): 부호
- 산술 연산자(*, /, %)
- 산술 연산자(+, -)
- 비교 연산자, in, is
- not
- and
- or

```python
print('aaple'[0] in 'add' and -3**3*0 > 4%2)
False
# 'a' in 'aad' : True
# 0 > 0 : False
```



# 표현식(expression)

#### 표현식(식)

- **식별자, 값, 연산자**로 구성 `a < 100` 

- 하나의 값

- `a = 10` 과 같은 할당문은 X

- 식별자가 값을 가지고 있는 경우 수식의 일부가 될 수 있다.

- `4 +` 와 같은 경우 하나의 값이 아니기 때문에 표현식이 아님

#### 문, 문장(statement)

- 파이썬이 **실행 가능한** 최소한의 코드 단위
  - `name = '` 와 같은 경우 문장X
- 모든 표현식(expression)은 문장(statement)
  - 표현식이 아닌 문장 존재: `del 5`, 할당문, 조건문, 반복문
- 즉, 문장이 표현식의 상위 개념
- `if a<3:` 조건문에서 `a<3` 은 표현식
