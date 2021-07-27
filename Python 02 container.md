# 컨테이너(Container)

- 여러 개의 값을 저장할 수 있는 것(객체)
- 시퀀스(sequence)형: 순서(**인덱스**)가 있는(orderd) 데이터 (**정렬X**)
  - 리스트(list), 튜플(tuple), 레인지(range), 문자형(string), 바이너리(binary)
- 비시퀀스(non-sequence)형 : 순서가 없는(unordered) 데이터
  - 세트(set), 딕셔너리(dictionary)



## 시퀀스형 컨테이너

### 리스트(list)

- **수정가능한(mutable)	순서(ordered)	순회 가능한(iterable)**
- 인덱스는 0부터 시작
- 대괄호([]) 또는 list()를 통해 생성
- 값에 대한 접근은 list[i]

```python
a = list((1, 2, 3))
print(a)
[1, 2, 3]

# 인덱스
print(a[0])
1

# 값 변경
a[0] = 'a'
print(a)
['a', 2, 3]

# 중첩 리스트
a = [[1, 'a'], ['b', 2]]
print(a[0][1])
'a'
```



### 튜플(tuple)

- 수정 불가능한(immutable)
- 소괄호(()) 또는 tuple()을 통해 생성
- 값에 대한 접근은 tuple[i]

```python
a = (1, 2, 3, 1)
print(a[1])
2

# 값 변경 불가능(TypeError)
a[1] = 'b'
TypeError: 'tuple' object does not support item assignment
```

- 값을 변경하지 못하기 때문에<br>직접 사용하는 경우는 많지 않으나<br>일반적으로 파이썬 내부에서 활용됨

  - multiple assignment
  - 함수에서 복수의 값을 반환하는 경우에도 활용

```python
x, y = 1, 2
print(x, y)
1 2

x, y = (1, 2)
print(x, y)
1 2

# 값 swap
x, y = 1, 2
x, y = y, x
print(x, y)
2 1

# 함수에서 복수의 값을 반환하는 경우
# divmod(a, b): a를 b로 나눈 (몫, 나머지)를 반환
print(divmod(5, 2))
(2, 1)
print(type(divmod(5, 2)))
<class 'tuple'>

x, y = divmod(5, 2)
print(x, y)
2 1

# 하나의 항목으로 구성된 튜플은 생성시 값 뒤에 콤마(,) 있어야 함
a = (1)
print(type(a))
<class 'int'>
b = (1,)
print(type(b))
<class 'tuple'>
```

  

### 레인지(range)

- 숫자의 시퀀스를 나타내기 위해 사용
  - 기본형<br>range(n) : 0부터 n-1까지
  - 범위지정<br>range(n, m): n부터 m-1까지
  - 범위 및 스텝 지정<br>range(n, m, s): n부터 m-1까지 s만큼 증가

```python
print(range(4))
range(0, 4)
print(list(range(4)))
[0, 1, 2, 3]
print(type(range(4)))
<class 'range'>

print(list(range(1, 5, 2)))
[1, 3]
print(list(range(6, 1, -1)))
[6, 5, 4, 3, 2]
# 범위와 스텝 방향이 맞지 않으면 값 없음
print(list(range(1, 3, -1)))
[]
print(list(range(2, 1)))
[]
```



### 시퀀스에서 활용하는 연산자/함수

#### containment test(포함 검사)

- 시퀀스 포함 여부 확인
  - in
  - not in

```python
print(1 in [2, 3])			#리스트
False
print(1 in (2, 3))			#튜플
False
print(-1 in range(3))		#레인지
False
print('a' in 'apple')		#문자열
True
print('b' not in 'apple')	#not in
True
```



#### concatenation(결합)

- 시퀀스 간의 연결/연쇄
- **range는 TypeError**

```python
print([1, 2]+['a'])		# 리스트
[1, 2, 'a']
print((1, 2)+('a',))  	
(1, 2, 'a')			# 튜플: 하나의 항목은 콤마 필요
print('12'+'b')			# 문자열
12b
```



#### 시퀀스 반복(*)

- **range는 TypeError**

```python
print([0]*5)			#리스트
[0, 0, 0, 0, 0]
print((1, 2)*3)			#튜플
(1, 2, 1, 2, 1, 2)
print('hi'*3)			#문자열
hihihi
```



#### 인덱싱(indexing)

- 시퀀스의 특정 인덱스 값에 접근
  - 해당 인덱스가 없는 경우 IndexError

```python
print([1, 2, 3][2])		#리스트
3
print((1, 2, 3)[0])		#튜플
1
print(range(3)[2])		#레인지
2
print('abc'[0])			#문자열
a
```



#### 슬라이싱(slicing)

```python
print([1, 2, 3, 4][1:3])
[2, 3]
print((1, 2, 3, 4)[:2])		#[:] 처음부터 끝까지
(1, 2)
print(range(10)[5:8])
range(5, 8)
print('abcd'[-3:-1]) 		#마지막 인덱스 = -1
bc

#세 번째는 간격
print([1, 2, 3, 4][:4:2])	
[1, 3]
print((1, 2, 3, 4)[1::3])
(2,)
print(range(10)[1:5:3])
range(1, 5, 3)
print('abcdefg'[-5::2])
ceg
```



#### 시퀀스의 길이 (len())

```python
print(len([1, 2, 3]))		#리스트
3
print(len((1, 2, 3)))		#튜플
3
print(len(range(100)))		#레인지
100
print(len('apple'))			#문자열
5
```



#### 최소/최대 (min()/max())

- 문자열은 ascii 코드에 따름
- ord() 함수로 확인
- ascii 코드로 문자열 확인은 chr()

```python
print(min([1, 100, 59]))	#리스트
1
print(max((-10, 20, 5)))	#튜플
20
print(max(range(-100, 2)))	#레인지
1
print(max('abcd1234%^!'))	#문자열
d
```



#### count

- 시퀀스에서의 특정 값의 개수
  - **값 없는 경우 0 반환**

```python
[1, 2, 1, 3, 4].count(1)	#리스트
(1, 2, 3, 1, 1).count(1)	#튜플
rnage(5).count(5)			#레인지
'apple'.count('p')			#문자열

2
3
0
2
```



#### 실습문제

```python
print(([1,2]*2 + ['apple', 'banana'])[4].count('a') in range(2, 5))

False
```







## 비시퀀스형 컨테이너

### 세트(set)

- 순서가 없는 자료구조
  - 중괄호({}) 또는 set()를 통해 생성
  - **빈 세트**를 만들기 위해서는 **set()** 사용해야 함
  - 순서가 없기 때문에 값에 접근 불가
- 수학에서 **집합**과 동일한 구조
  - **집합 연산** 가능
  - **중복된 값 존재X**

```python
print({1, 2, 3, 1, 2})			#중복 값 제거
{1, 2, 3}
print(type({}))					#{}는 딕셔너리
<class 'dict'>
print(type(set()))				# 빈 세트 만들기는 set()
<class 'set'>
```

- 집합 연산

```python
set_a = {1, 2, 3}
set_b = {3, 4, 5}
print(set_a - set_b)			#차집합
{1, 2}
print(set_a | set_b)			#합집합
{1, 2, 3, 4, 5}
print(set_a & set_b)			#교집합
{3}
```

* 세트(set) 활용

  * 리스트에서 중복 값 제거(정렬은 안됨)
  * 즉, 순서가 중요한 경우 사용하면 안됨

  ```python
  lst = [1, 2, 1, 2, 3]		#리스트
  print(set(lst))				#set()으로 중복 값 제거(정렬은 안됨)
  {1, 2, 3}
  print(len(set(lst)))		#중복 값 제거 후 개수 구하기
  3
  ```

  

### 딕셔너리(dictionary)

- key와 value가 쌍으로 이뤄진 자료구조
  - 중괄호({}) 또는 dict()를 통해 생성
  - key를 통해 value에 접근

```python
dic = {}
dic2 = dict()
print(type(dic))
<class 'dict'>
print(type(dic2))
<class 'dict'>

dic = {'a': 'apple', 'b':'banana', 'num': [1, 2, 3]}
print(dic['num'])				
[1, 2, 3]
# key로 value 값에 접근 후
# value가 리스트면 인덱스, 딕셔너리면 key로 접근 가능
print(dic['num'][1])		
2
```

- **key는 변경 불가능한 데이터(immutable)만 가능**
  - string, integer, float, boolean, tuple, range
  - 리스트(list)는 불가능
- value는 모든 값으로 설정 가능(list, dictinoary 등)



## 컨테이너 특징

### 컨테이너 형변환

- 컨테이너: string, list, tuple, range, set, dictionary

- **모든 컨테이너는 range, dictionary로 형변환 불가**

- **딕셔너리는 string으로 형변환 가능**

  ```python
  a = {1:'a', 2:'b'}
  print(str(a))
  {1:'a', 2:'b'}
  print(type(str(a)))
  <class 'str'>
  ```

  - **list, tuple, set으로는 key만 가능**

  ```python
  a = {1:'a', 2:'b'}
  print(list(a))
  [1, 2]
  print(type(list(a)))
  <class 'list'>
  ```

  

### 컨테이너 분류

#### 변경 불가능한 데이터(immutable)

- 리터럴(literal)-숫자(Number), 문자열(String), 참/거짓(Bool)
- range
- tuple

#### immutable의 복사

```python
a = 20
b = a		# b에 20이 할당됨
b = 10 		# b에 10이 (재)할당됨, a에는 영향없음
```

#### 변경 가능한 데이터(mutable)

- list
- set
- dictionary

#### mutable의 복사

```python
lst1 = [1, 2, 3]	#lst1은 [1, 2, 3] 리스트를 참조함
lst2 = lst1			#lst2에 할당이 아닌 lst2가 [1, 2, 3] 리스트 참조
lst2[0] = 10		#리스트가 [10, 2, 3]으로 바뀌고
print(lst1)			#리스트를 참조하는 lst1과 lst2는 같은 결과를 보여줌
[10, 2, 3]
print(lst2)
[10, 2, 3]
```

http://pythontutor.com/에서 확인해 볼것

#### 정리

컨테이너

- 시퀀스(ordered)
  - 'String'		(immutable)
  - [list] 			   **(mutable)**
  - (tuple) 		(immutable)
  - range()		(immutable)

- 비시퀀스(Unordered)
  - {set}				**(mutable)**
  - dictionary	   **(mutable)**

