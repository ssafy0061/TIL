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

