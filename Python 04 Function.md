# 함수 Function

### 함수의 특징

- 특정한 기능을 하는 코드의 조각(묶음)
- **높은 재사용성**
  - 하나의 큰 프로그램을 여러 부분으로 나누어 같은 함수를 여러 상황에서 호출
- **유지보수 용이**
  - 일부분을 수정하기 쉽다



#### 함수의 구성요소

- **이름**
- **매개변수(parameters)**
- **바디(body: 실행될 코드 블록)**
- 독스트링(Docstring: 함수 설명 등을 선택적으로 추가) 및 코드셋
- **반환값**(return)

```python
def name(parameters)	#def는 함수 선언할 때 사용
"""						#큰따옴표(") 3개
Docsting(Document String): 함수나 클래스의 기능을 설명함 			
"""		
body					#함수 내용
return	반환값		  				
```



#### 내장 함수(Built-in Functions)

- 파이썬에는 항상 사용할 수 있는 함수와 형(type)이 내장돼 있음

bool(), chr(), dir(), float(), format(), id(), input(), len(), list(), max()j, min() 등



#### 함수의 선언

- 함수의 선언은 def 키워드를 이용
- 들여쓰기를 통해 함수 body(실행될 코드 블록)를 작성
  - Docsting은 함수 body 앞에 선택적으로 작성 가능
  - 작성할 때 반드시 첫번째 문장에 문자열 """ """
- 함수는 매개변수(parameter)늘 넘겨줄 수 있음
- 함수는 동작 후에 return을 통해 결과값을 전달함
  - 반드시 하나의 객체를 반환(return이 없으면 None 반환)

#### 함수의 호출

- 함수는 함수명()으로 호출
  - 매개변수가 있는 경우, 함수명(인수1, 인수2, ...)로 호출
  - 함수 선언할 때는 매개변수, 호출할 때는 인수<br>(매개변수와 인수는 똑같이 쓰이기 때문에 혼용해서 언급하기도 함)

```python
def a_sum(x, y):
    return x + y

print(a_sum(1, 2))		#print()로 눈에 볼 수 있게 출력
3
```

- **함수는 호출되면 코드를 실행하고** 
- **return 값을 반환하며 종료**

예시

```python
num1 = 0
num2 = 1

def func1(a, b):
    return a + b

def func2(a, b):
    return a - b

def func3(a, b):
    return func1(a, 5) + func2(5, b)	#func1, func2 함수 호출

result = func3(num1, num2)				#fucn3 함수 호출
print(result)
```

- 선언을 해야 호출가능

```python
def func3(a, b):
    return func1(a, 5) + func2(5, b)

def func1(a, b):
    return a + b

def func2(a, b):
    return a - b
```

- func3이 func1, 2보다 먼저 선언돼도<br>func3 호출전에 func1, 2가 선언되면 결과 정상적으로 나옴



세제곱 함수

```python
def cube(number):
    return number ** 3

print(cube(2))
8
print(cube(100))
1000000
```



### 함수 output

#### return

- 모든 함수는 반환 값이 존재

  - 어떠한 객체라도 상관없음

- 오직 한 개의 객체만 return됨

- return 다음에 값 2개를 적으면 **tuple로 반환**(1개의 객체)

  - ```python
    def A(a, b):
        return a+b, a-b
    print(A(1, 2))
    (3, -1)
    ```

- 명시적인 return 값이 없는 경우 **None 반환**



- ##### 주의사항 return vs print

  - return은 함수 안에서만 사용되는 키워드
  - print는 출력을 위해 사용되는 함수
  - jupyter notebook처럼 REPL(Read Eval Print Loop)환경에서는<br>마지막으로 작성된 코드의 return 값을 보여주므로 같은 동작을 하는 것으로 착각할 수 있음

##### 예제) 사격형 넓이, 둘레 계산

```python
def rectangle(width, height):
    area = width * height
    perimeter = 2 * (width + height)
    return area, perimeter
print(rectangle(30, 20))
(600, 100)
```



### 함수 input

#### 위치인자(Positional Arguments)

- 기본적으로 함수 호출 시 인자는 위치에 따라 함수 내에 전달됨
- 일반적으로 많이 보는 인자

```python
# parameter(매개변수)
# 함수에 입력으로 전달된 '값을 받는' 변수
def my_func(a, b):
    pass
# arugument({전달}인자, 인수)
# 함수를 호출할 때 함수에 전달하는 '입력 값'
my_func(1, 2)
```



#### 기본 인자 값(Defalut Arguments Values)

- 기본값을 지정하여 함수 호출 시 인자 값을 설정하지 않도록 함
  - 정의 된 것보다 더 적은 개수의 인자들로 호출 가능

```python
def add(x, y=1):	#기본 인자 값: y=1
    return x + y
print(add(2))
3
print('a', end='\n') #기본 인자 값:end='\n'
```



#### 키워드 인자(keyword Arguments)

- 직접 변수의 이름으로 특정 인자를 전달 가능
- 키워드 인자 다음에 위치 인자오면 Error

```python
def add(x, y):
    return x + y

add(x=2, 1)			#키워드 인자 다음에 위치 인자는 Error
SyntaxError: positional argument follows keyword argument
add(x=2, y=1)
3
add(2, y=2)
4
```

- **기본 인자값**은 함수 선언할 때, 키워드 인자는 호출 할 때



#### 가변 인자 리스트(Arbitrary Argument Lists)

- 함수가 임의의 개수 인자로 호출될 수 있도록 지정
- 인자들은 tuple로 묶여 처리되며, 매개변수에 *(asterisk)를 붙여 표현

```python
def add(*args):		# 가변 인자 리스트는 관습적으로 '*args'를 씀
    for arg in args:
        print(arg)
        
print(add(2))		# 가변 인자는 필수x
2
print(add(2, 3, 4, 5))
2
3
4
5

def add(*args):		# 가변 인자 리스트 그대로 쓸 때
    print(args)
        
add(2)
(2,)				# tuple인 것을 알 수 있다.
add(2, 3, 4, 5)
(2, 3, 4, 5)
```



#### 가변 키워드 인자(Arbitrary Keyword Arguments)

- 함수가 임의의 개수 인자를 키워드 인자로 호출될 수 있도록 지정
- 인자들은 dictionary로 묶여 처리되며, 매개변수에 **를 붙여 표현

```python
def family(**kwargs):  #관습적으로 '**kwargs' 사용
    return kwargs
    
print(family(father='John', mother='Jane', me='John Jr.'))
{'father': 'John', 'mother': 'Jane', 'me': 'John Jr.'}
```



#### 함수 정의(선언) 주의사항

- 기본 인자 값을 가지는 인자 다음에<br>기본 값이 없는 인자로 정의할 수 없음
  - SyntaxError: non-default argument follows default argument

#### 함수 호출 주의사항

- 키워드 인자 다음에 위치 인자를 활용할 수 없음
  - SyntaxError: positional argument follows keyword argument

- 가변 인자 리스트가 위치 인자보다 앞쪽에 올 수 없음

```python
def add(*args, x):
   pass

add(1, 2, 3)
# 1, 2, 3 중에 어디까지 args인지 알 수 없음
```

- 가변 키워드 인자가 위치 인자보다 앞쪽에 올 수 없음

- 위치인자,  *args, **kwargs를 함께 사용했을 때 올바른 순서

  ```python
  my_info(x, *args, **kwargs)
  ```

