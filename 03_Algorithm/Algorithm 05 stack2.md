# 5. 스택2

- 계산기
- 백트래킹
- [참고] 부분집합, 순열
- 분할정복



## 계산기

- 문자열로 된 계산식이 주어질 때, 스택을 이용하여 이 계산식의 값을 계산할 수 있다.
- 문자열 수식 계산의 일반적 방법
  - step1. 중위 표기법의 수식을 후위 표기법으로 변경한다.(스택이용)
    - 중위 표기법(infix notation)
       - 연산자를 피연산자의 가운데 표기하는 방법
       - 예) A + B
  - step2. 후위 표기법의 수식을 스택을 이용하여 계산한다.
    - 후위 표기법(postfix notation)
      - 연산자를 피연산자 뒤에 표기하는 방법
      - 예) AB+



### step1. 중위표기식의 후위표기식 변환

#### 방법 1

- 수식의 각 연산자에 대해서 우선순위에 따라 괄호를 사용하여 다시 표현한다.

- 각 연산자를 그에 대응하는 오른쪽 괄호의 뒤로 이동시킨다.

- 괄호를 제거한다.

  ```
  예) A*B-C/D
  1단계: ((A*B)-(C/D))
  2단계: ((AB)*(CD)/)-
  3단계: AB*CD/-
  ```



#### 방법2(스택을 이용한 알고리즘)

- 입력 받은 중위 표기식에서 토큰을 읽는다.
- 토큰이 피연산자이면 토큰을 출력
- 토큰이 연산자(괄호포함)일 때, 
  - 이 토큰이 스택의 top에 저장되어 있는 연산자보다
    - 우선순위가 높으면 스택에 push, 
    - 그렇지 않으면 
      - 스택에 top이 토큰보다 우선순위가 낮지 않으면(높거나 같으면) pop
      - 우선순위 낮은 연산자가 top이면 토큰의 연산자를 push한다. 
  - 만약 top에 연산자가 없으면 push한다.
- 토큰이 오른쪽 괄호 ')'이면 스택 top에 왼쪽 괄호'('가 올 때까지 스택에 pop연산을 수행하고 pop 한 연산자를 출력한다. 
  - 왼쪽 괄호를 만나면 pop만 하고 출력하지 않는다.
- 중위 표기식에 더 읽을 것이 없다면 중지
  - 더 읽을 것이 있다면 처음부터 다시 반복
- 스택에 남아 있는 연산자를 모두 pop하여 출력
  - 스택 밖의 왼쪽 괄호는 우선순위가 가장 높으며, 스택 안의 왼쪽 괄호는 우선순위가 가장 낮다

```
icp(in-coming priority)
isp(in-stack priority)

if (icp>isp) push()
else pop()
```

| 토큰 | isp  | icp  |
| ---- | ---- | ---- |
| )    | -    | -    |
| *, / | 2    | 2    |
| +, - | 1    | 1    |
| (    | 0    | 3    |



### step2. 후위 표기식 계산

#### 스택 이용

- 피연산자를 만나면 스택에 push
- 연산자를 만나면 필요한 만큼의 피연산자를 스택에서 pop하여 연산하고, 
  - 연산결과를 다시 스택에 push
- 수식이 끝나면 마지막으로 스택을 pop하여 출력





## 백트래킹

- 백트래킹(Backtracking) 기법은
  - 해를 찾는 도중에 '막히면'(즉, 해가 아니면) 되돌아가서 다시 해를 찾아가는 기법
- 최적화(optimization) 문제와 결정(decision)문제를 해결할 수 있다.
- 결정문제: 문제의 조건을 만족하는 해가 존재하는지 여부를 'yes' 또는 'no'가 답하는 문제
  - 미로문제
  - n-Queen 문제
  - Map coloring
  - 부분집합의 합(Subset Sum) 문제 등



### 미로찾기

- 입구와 출구가 주어진 미로에서 입구부터 출구까지의 경로를 찾는 문제
- 이동 가능 방향은 4방향



### 백트래킹과 깊이우선탐색과의 차이

- 어떤 노드에서 출발하는 경로가 해결책으로 이어질 것 같지 않으면 더 이상 그 경로를 따라가지 않음으로써 시도의 횟수를 줄임(Prunning 가지치기)

- 깊이 우선탐색이 모든 경로를 추적하는 데 비해

  - 백트래킹은 불필요한 경로를 조기에 차단

- 깊이 우선탐색을 하기에는 경우의 수가 너무 많음

  - 즉, N! 가지의 경우의 수를 가진 문제는 깊이우선탐색으로 처리 불가

- 백트래킹 알고리즘을 적용하면

  - 모든 후보를 검사하지 않으므로
  - 일반적으로 경우의 수가 줄어들지만
  - 이 역시 최악의 경우에는 여전히 지수함수 시간(Exponential Time)을 요하므로 처리 불가능

  

### 백트래킹 기법

- 어떤 노드의 유망성을 점검한 후에
  - 유망(promising)하지 않다고 결정되면 그 노드의 부모로 되돌아가(backtracking) 다음 자식 노드로 감
- 어떤 노드를 방문했을 때 그 노드를 포함한 경로가 해답이 될 수 없으면 그 노드는 유망하지 않다고 하여, 반대로 해답의 가능성이 있으면 유망하다고 한다.
- 가지치기(pruning): 유망하지 않는 노드가 포함되는 경로는 더 이상 고려하지 않는다.

### 백트래킹을 이용한 알고리즘 절차

- 상태 공간 트리의 깊이 우선 검색(DFS)을 실시
- 각 노드가 유망한지 점검
- 만일 그 노드가 유망하지 않으면, 그 노드의 부모 노드로 돌아가서 검색을 계속함

- 즉, 모든 노드를 보는 DFS보다 경우의 수가 줄어듦



## [참고] 

## 부분집합 구하기

- powerset
  - 어떤 집합의 공집합과 자기자신을 포함한 모든 부분집합
  - 구하고자 하는 어떤 집합의 원소가 n일 경우 부분집합의 개수는 2^n이 나온다.

### 백트래킹 기법으로 powerset 구하기

- 앞에서 한 일반적인 백트래킹 접근 방법 이용
- n개의 원소가 들어있는 집합의 2^n개의 부분집합을 만들 때<br>true 또는 false값을 가지는 항목들로 구성된 n개의 배열을 만드는 방법 이용
- 여기서 배열의 i번째 항목은 i번째의 원소가 부분집합의 값인지 아닌지를 나타내는 값이다.

#### 각 원소의 부분집합에 포함여부 확인하고 부분집합 생성하기

```
bit = [0, 0, 0, 0]
for i in range(2):
	bit[0] = i
	for j in range(2):
		bit[1] = j
		for k in range(2):
			bit[2] = k
			for l in range(2):
				bit[3] = 1
				print(bit)
```

#### powerset을 구하는 백트래킹 알고리즘

```
def backtrack(a, k, input):
	global MAXCANDIDATES
	c = [0] * MAXCANDIDATES
	
	if k == input:
		process_solution(a, k) #답이면 원하는 작업을 한다.
	else:
		k += 1
		ncandidates = construct_candidates(a, k, input, c)
		for i in range(ncandidates):
			a[k] = c[i]
			backtrack(a, k, input)

def construct_candidates(a, k, input, c):
	c[0] = True
	c[1] = False
	return 2

MAXCANDIDATES = 100
NMAX = 100
a = [0] * NMAX
backtrack(a, 0, 3)
```



## 순열 만들기

- 예) {1, 2, 3}을 포함하는 모든 순열을 생성하는 함수

  - 123, 132, 213, 231, 312, 321 총 6가지

  - ```
    f(i, N)
    	if i==N		#순열 완성
    	
    	else
    		for j: i -> N-1
    			P[i] <-> P[j]
    			f(i+1, N)
    			P[i] <-> P[j]	
    ```

    교수님 풀이

    ```python
    def f(i, N):
        if i==N:	#순열 완성
            print(P)
        else:		#i번 원소값 결정
            for j in range(i, N):	# 자신부터 오른쪽 원소와 교환
                P[i], P[j] = P[j], P[i]
                f(i+1, N)
                P[i], P[j] = P[j], P[i]
     
    P = [1, 2, 3, 4, 5]
    f(0, len(P))
    
    ##### r개인 순열 출력하기
    def f(i, N, r):
        if i==N:	#순열 완성
            print(P[:r])
        else:		#i번 원소값 결정
            for j in range(i, N):	# 자신부터 오른쪽 원소와 교환
                P[i], P[j] = P[j], P[i]
                f(i+1, N, r)
                P[i], P[j] = P[j], P[i]
     
    P = [1, 2, 3, 4, 5]
    f(0, len(P), 3)
    ```

    

- 동일한 숫자가 포함되지 않았을 때, 각 자리수 별로 loop을 이용해 다음과 같이 구현할 수 있다.

```
for i1 in range(1, 4):
	for i2 in range(1, 4):
		if i2 1= i1:
			for i3 in range(1, 4):
				if i3 != i1 and i3 != i2:
					print(i1, i2, i3)
```

#### 백트래킹을 이용하여 순열 구하기

```
def backtrack(a, k, input):
	global MAXCANDIDATES
	c = [0] * MAXCANDIDATES
	
	if k == input:
		for i in range(1, k+1):
			print(a[i], end=' ')
		print()
	else:
		k += 1
		ncandidates = construct_candidates(a, k, input, c)
		for i in range(ncandidates):
			a[k] = c[i]
			backtrack(a, k, input)

def construct_candidates(a, k, input, c):
	in_perm = [Fasle] * NMAX
	
	for i in range(1, k):
		in_perm[a[i]] = True
		
	ncandidates = 0
	for i in range(1, input+1):
		if in_perm[i] == Fasle:
			c[ncandidates] = i
			ncandidates += 1
			
	return ncandidates
```



## 예제

- {1, 2, 3, 4, 5, 6, 7, 8, 9, 10}의 powerset 중 원소의 합이 10인 부분집합 구하기



### 부분집합의 합

- A[i]원소를 부분 집합의 원소로 고려하는 재귀함수(A는 서로 다른 자연수의 집합)

```
# i-1원소까지 고려한 합 s, 찾으려는 합 t

f(i, N, s, t)
	if s == t			#i-1원소까지의 합이 찾는 값인 경우
	...
	elif i == N			# 모든 원소에 대한 고려가 끝난 경우
	...
	elif s > t			# 남은 원소를 고려할 필요가 없는 경우
	...
	else				# 남은 원소가 있고 s<t인 경우
		subset[i] = 1
		f(i+1, N, s+A[i], t)	#i원소 포함
		subset[i] = 0
		f(i+1, N, s, t)			#i원소 미포함
```



#### 추가 고려사항

- 고려한 구간의 합 S > T(목표 합 )이면 중단

- 남은 구간의 합 RS

  - S+RS <T

  - 남은 원소의 합을 다 더해도 찾는 값 T미만인 경우 중단

  - RS 구하는 방법

    - 첫항이 0인 경우 첫항에서의 RS는 전체의 합

    - ```
      f(i+1, N, s+A[i], RS-A[i])
      f(i+1, N, s, RS-A[i])
      ```

      

# 분할 정복 알고리즘

- 유래
  - 1805년 12월 2일 아우스터리츠 전투에서 나폴레옹이 사용한 전략
  - 전력이 우세한 연합군을 공격하기 위해 나폴레옹은 연합군의 중앙부로 쳐들어가 연합군을 둘로 나눔
  - 둘로 나뉜 연합군을 한 부분씩 격파함
- 설계전략
  - 분할(Divide): 해결할 문제를 여러 개의 작은 부분으로 나눈다.
  - 정복(Conquer): 나눈 작은 문제를 각각 해결한다.
  - 통합(Combine): (필요하다면)해결된 해답을 모은다.

### 예제

#### 거듭제곱(Exponentiation)

- O(n)

```
def Power(base, Exponent):
	if base == 0: return 1
	result = 1		# base 0은 1이므로
	for i in range(Exponent):
		result*=Base
	return result
```

#### 분할정복 기반의 알고리즘

- O(log2n)

```
def Power(Base, Exponent):
	if Exponent == 0 or Base == 0
		return 1
	if Exponent % 2 == 0:
		NewBase = Power(Base, Exponent/2)
		return NewBase*NewBase
	else:
		NewBase = Power(Base, (Exponent-1)/2)
		return (NewBase*NewBase)*Base
```

