# 제어문(Control Statement)

- 파이썬은 기본적으로 위에서부터 아래로 순차적으로 명령 수행
- 특정 상황에 따라 코드를 선택적으로 실행(분기/조건)하거나 계속하여 실행(반복)하는 제어가 필요함
- 제어문은 순서도(flow chart)로 표현 가능



# 조건문(Conditional Statement)

- if문은 참/거짓을 판단할 수 있는 조건식과 함께 사용
- 표현식(expression)에는 참/거짓에 대한 조건식
- 조건이 참인 경우 이후 들여쓰기(띄어쓰기 4칸) 되어있는 코드 블럭을 실행

- 이외의 경우 else 이후 들여쓰기(띄어쓰기 4칸) 되어있는 코드 블럭을 실행

```python
if <expression>:
    # 참인 경우 code block
else:
    # 거짓인 경우 code block
```

예제) **조건문을 통해 변수 num의 홀수/짝수 여부 판단**

```python
num = int(input('숫자 입력: '))
if num % 2:  # num % 2 == 1:
    print('홀수')
else:
    print('짝수')
```

### 복수 조건문, 중첩 조건문

```python
#미세먼지 농도에 따른 등급
if dust > 150:
    print('매우나쁨')
    if dust > 300:				# 중첩 조건문
        print('실외 활동 자제')
elif dust > 80:    				# 복수 조건문: 조건이 여러개일 때 elif
    print('나쁨')
elif dust > 30:
    print('보통')
else:
    print('좋음')
```

### 조건 표현식(Conditional Expression)

- 조건 표현식을 일반적으로 조건에 따라 값을 정할 때 활용
- 삼항 연산자(Ternary Operator)로 부르기도 함

```python
<True인 경우 값> if <expression> else <False인 경우 값>

# 절대값
value = num if num >= 0 else -num		
# 콜론(:)없음, 할당은 한번만
# 참일 경우 num, 거짓일 겨우 -num을 할당

# 홀수, 짝수
result = '홀수입니다.' if num % 2 else '짝수입니다.'
```

- 코드는 짧아지나 스타일가이드에서는<br>코드의 길이와 상관없이 의미하는 바를<br>누구나 잘 인식할 수 있어야 한다고 안내함
- 즉, 가독성이 떨어지기 때문에 권장하지 않음



# 반복문(Loop Statement)

- while 문
  - 종료조건 필수
- for 문
  - 반복가능한(순회가능 = iterable) 객체를 모두 순회하면 종료(종료조건 필요X)
- 반복 제어
  - break, continue, for-else

### while문

- 조건식이 참인 경우 반복적으로 코드 실행
  - 조건이 참인 경우 들여쓰기 되어있는 코드 블록 실행
  - 코드 블록 모두 실행되고, 다시 조건식을 검사하여 반복
  - while문은 무한 루프를 하지 않도록 종료조건 필수

```python
while <expression>:
    # Code block
    
# 1부터 사용자가 입력한 양의 정수까지의 총합
n = 0
total = 0
user_input = int(input())

while n <= user_input:
    total += n
    n += 1
print(total)
```



### for문

- 시퀀스(string, tuple, list, range)를 포함한<br> 순회가능한(iterable) 객체요소를 모두 순회함
  - 처음부터 끝까지 모두 순회하므로 별도의 종료조건 필요없음

```python
for <변수명> in <iterable>:
    # Code block

# 입력한 문자열을 한글자씩 출력
chars = 'happy'
for char in chars:			#시퀀스 객체 변수명은 복수형으로,
    print(char)				#변수명도 의미하는 바를 알기 쉽게 짓기
h
a
p
p
y
```



# 실습/ 활용방법

### 조건/반복문 실습문제

- 반복문과 조건문만 활용하여 1~30까지 숫자 중에 홀수만 출력

```python
for i in range(1, 31):
    if i % 2:
        print(i)
```



### 리스트 순회하기

- 리스트 순회하며 index값을 같이 출력하기

```python
members = ['a', 'b', 'c']

for i in range(len(members)):
    print(f'{i+1}번 {members[i]}')
1번 a
2번 b
3번 c

#range(n): 0부터 n-1까지
#list[n]:리스트에서 index n의 값 접근
#index는 0부터 시작(끝에서부터 시작은 -1)
```



### 내장함수 enumerate(iterable, start = 0)

[파이썬 공식 문서 참고](https://docs.python.org/3/library/functions.html#enumerate)

```python
members = ['a', 'b', 'c']
print(enumerate(members))
<enumerate object at 0x000002A7B5796840>
print(list(enumerate(members))
[(0, 'a'), (1, 'b'), (2, 'c')]
print(enumerate(members, start=1))
[(1, 'a'), (2, 'b'), (3, 'c')]
      
# enumerate 내장함수 
#(index, value)형태의 tuple로 구성된 열거 객체 반환
for idx, member in enumverate(members):
    print(idx, member)
0 a
1 b
2 c
```



# 반복문 제어

- berak
  - 반복문 종료
- continue
  - continue 이후의 코드 블록은 수행하지 않고 다음 반복 수행
- for-else
  - 끝까지 반복문 실행 후 else문 실행
  - break를 통해 중간에 종료되는 경우 else문은 실행X

### break

```python
# 반복문 종료
n = 0
while True:
    if n == 3:
        break
    print(n)
    n += 1
    
0
1
2
```



### continue

```python
# continue 이후의 코드 블록은 수행하지 않고 다음 반복 수행
for i in range(6):
    if i % 2 == 0:
        continue
    print(i)
1
3
5
```



### for-else

```python
# 끝까지 반복문 실행 후 else문 실행
# break를 통해 중간에 종료되는 경우 else문은 실행X

#1
for char in 'apple':
    if char == 'b':
        print('b!')
        break
else:
    print('b가 없음')
b가 없음

#2
for char in 'banana':
    if char == 'b':
        print('b!')
        break
else:
    print('b가 없음')
b!
```



### pass

- 아무것도 하지 않음
  - 반복문 아니어도 사용 가능
  - 임시로 자리 채우는 용도

```python
# pass
for i in range(5):
    if i == 3:
        pass
    print(i)
0
1
2
3
4

# continue
for i in range(5):
    if i == 3:
        continue
    print(i)
0
1
2
4
```

