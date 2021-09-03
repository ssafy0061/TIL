# 6. 큐(Queue)

- 선형큐
- 원형큐
- 연결큐
- 우선순위 큐
- 큐의 활용: 버퍼
- BFS



## 큐

### 큐(Queue)의 특성

- 스택과 마찬가지로 삽입과 삭제의 위치가 제한적인 자료구조

  - 큐의 뒤에서는 삽입만 하고

    - 꼬리(Rear)
    - 저장된 원소 중 마지막 원소

  - 큐의 앞에서는 삭제만 이루어지는 구조

    - 머리(Front)

    - 저장된 원소 중 첫 번째 원소(또는 삭제된 위치)

      

- 선입선출구조(FIFO: First In First Out)

  - 큐에 삽입한 순서대로 원소가 저장되어, 가장 먼저 삽입(First In)된 원소는 가장 먼저 삭제(First Out)된다.
  - 예) 서비스 대기행렬(줄서기)



- 큐의 기본연산
  - 삽입: enQueue
  - 삭제: deQueue



### 주요 연산

| 연산          | 기능                                                |
| ------------- | --------------------------------------------------- |
| enQueue(item) | 큐의 뒤쪽(rear 다음)에 원소를 삽입하는 연산         |
| deQueue()     | 큐의 앞쪽(front)에서 원소를 삭제하고 반환하는 연산  |
| createQueue() | 공백 상태의 큐를 생성하는 연산                      |
| isEmpty()     | 큐가 공백상태인지를 확인하는 연산                   |
| isFull()      | 큐가 포화상태인지를 확인하는 연산                   |
| Qpeek()       | 큐의 앞쪽(front)에서 원소를 삭제 없이 반환하는 연산 |



- 연산 과정(선형 큐)

  - 공백 큐 생성: createQueue();

    - front = rear = -1  (인덱스 0의 왼쪽 칸)

    - ```
      Q = [0]*N
      front = -1
      rear = -1
      ```

  - 원소 A 삽입: enQueue(A);

    - front = -1, rear는 인덱스 0

    - ```
      rear += 1
      Q[rear] = 'A'	#enQueue(A)
      ```

  - 원소 B 삽입: enQueue(B);

    - front = -1, rear는 인덱스 1

    - ```
      rear += 1
      Q[rear] = 'B'	#enQueue(B)
      ```

  - 원소 반환/삭제: deQueue();

    - 인덱스 0에 있던 A가 삭제/반환되고 인덱스 0이 front가 됨

    - rear는 그대로 인덱스 1

    - ```
      front += 1
      # 함수안이라면
      data = Q[front]
      return data
      ```

  - 원소 C 삽입: enQueue(C);

    - front는 인덱스 0, rear는 C가 저장된 인덱스 2

  - 원소 반환/삭제: deQueue();

    - front는 인덱스1(B가 삭제/반환된 자리), rear는 그대로 인덱스 2

  - 원소 반환/삭제: deQueue();

    - front와 rear 모두 인덱스 2 (큐가 빈 상태)

## 선형큐

- 1차원 배열을 이용한 큐
  - 큐의 크기 = 배열의 크기
  - front: 저장된 첫 번째 원소의 인덱스
  - rear: 저장된 마지막 원소의 인덱스
- 상태 표현
  - 초기 상태: front = rear = -1
  - 공백 상태: front = rear
  - 포화 상태: rear = n-1 (n: 배열의 크기, n-1: 배열의 마지막 인덱스)

### 구현

#### 초기 공백 큐 생성

- 크기 n인 1차원 배열 생성
- front와 rear를 -1로 초기화

#### 삽입: enQueue(item)

- 마지막 원소 뒤에 새로운 원소를 삽입하기 위해

  - rear 값을 하나 증가시켜 새로운 원소를 삽입할 자리를 마련
  - 그 인덱스에 해당하는 배열원소 Q[rear]에 item을 저장

  ```
  def enQueue(item):
  	global rear
  	# 디버깅용, 실제로는 넘치지 않게 크기 조절해야 함
  	if isFull(): print("Queue_Full")	
  	else:
  		rear <- rear + 1;
  		Q[rear] <- item;
  ```

#### 삭제: deQueue()

- 가장 앞에 있는 원소를 삭제하기 위해

  - front값을 하나 증가시켜 큐에 남아있게 될 첫 번째 원소로 이동
  - 새로운 첫 번째 원소를 리턴 함으로써 삭제와 동일한 기능함

  ```
  deQueue()
  	if(isEmpty()) then Queue_Empty();    # 디버깅용
  	else{
  		front <- front + 1;
  		return Q[front];
  	}
  ```

#### 공백상태 및 포화상태 검사: isEmpty(), isFull()

- 공백상태: front = rear

- 포화상태: rear = n-1 (n: 배열의 크기, n-1: 배열의 마지막 인덱스)

  ```
  def isEmpty():
  	return front == rear
  	
  def Full():
  return rear == len(Q) - 1
  ```

#### 검색: Qpeek()

- 가장 앞에 있는 원소를 검색하여 반환하는 연산

- 현재 front의 한자리 뒤(front+1)에 있는 원소, 즉 큐의 첫 번째에 있는 원소를 반환

  ```
  def Qpeek():
  	if isEmpty(): print("Queue_Empty")
  	else: return Q[front+1]
  ```

  

#### 예제

- 큐 구현하여 동작 확인하기
  - 세 개의 데이터 1, 2, 3을 차례로 큐에 삽입하고
  - 큐에서 세 개의 데이터를 차례로 꺼내서 출력
    - 1, 2, 3

```python
Q = [0] * 10	#10칸 짜리 큐
front = -1
rear = -1

rear += 1
Q[rear] = 1		#enQueue(1)

rear += 1
Q[rear] = 2		#enQueue(2)

rear += 1
Q[rear] = 3		#enQueue(3)

while front != rear:
    front += 1
    print(Q[front], end= ' ')	#print(deQueue())
print()
# 결과
1 2 3


# 방법2(위보다 느림, append는 끝에 추가하는 것이 아니고 리스트를 새로 만듦)
listQ = []
listQ.append(1)
listQ.append(1)
listQ.append(1)
whlie listQ:
    print(listQ.pop(0), end =' ')
print()
# 결과
1 2 3

## 즉, 간단한 문제는 list.append로
##본격적인 방식은 방법 1의 방식으로
```



[참고] 속도는 중간정도

```python
from collections import deque

# enqueue -> append  		<-> appendleft(왼쪽에 추가)
q = deque()
q.append(1)
q.append(2)
q.append(3)
# dequeue -> popleft
while q:
    print(q.popleft())
#결과
1
2
3
```



### 문제점

#### 잘못된 포화상태 인식

- 선형 큐를 이용하여 원소의 삽입과 삭제를 계속할 경우
  - 배열의 앞부분에 활용할 수 있는 공간이 있음에도 불구하고
  - rear=n-1인 상태 즉, 포화상태로 인식하여 더 이상의 삽입을 수행하지 않게 됨

#### 해결방법1

- 매 연산이 이루어질 때마다 저장된 원소들을 배열의 앞부분으로 모두 이동시킴
  - front = -1
  - rear = 마지막 원소 인덱스 위치(없으면 -1)
- 원소 이동(복사)에 많은 시간이 소요되어 큐의 효율성이 급격히 떨어짐

#### 해결방법2(원형큐)

- 1차원 배열을 사용하되
  - 논리적으로는 배열의 처음과 끝이 연결되어 원형형태의 큐를 이룬다고 가정하고 사용
  - 즉, 인덱스 n-1 다음은 0이 이어짐



## 원형큐

### 구조

- 초기 공백 상태

  - front = rear = 0

- Index의 순환

  - front와 rear의 위치가 배열의 마지막 인덱스인 n-1를 가리킨 후,<br>그 다음에는 논리적 순환을 이루어 배열의 처음 인덱스인 0으로 이동해야 함

  - 이를 위해 나머지 연산자 mod를 사용함

    - ```
      (rear+1)%N
      ```

- front 변수

  - 공백 상태와 포화 상태 구분을 쉽게 하기 위해 front가 있는 자리는 사용하지 않고 항상 빈자리로 둠

- 삽입 위치 및 삭제 위치

  |        | 삽입 위치             | 삭제 위치               |
  | ------ | --------------------- | ----------------------- |
  | 선형큐 | rear = rear + 1       | front = front + 1       |
  | 원형큐 | rear = (rear+1) mod n | front = (front+1) mod n |

### 구현

#### 초기 공백 큐 생성

- 크기 n인 1차원 배열 생성
- front와 rear를 0으로 초기화

#### 공백상태 및 포화상태 검사: isEmpty(), isFull()

- 공백상태: front = rear
- 포화상태: 삽입할 rear의 다음 위치 = 현재 front
  - (rear+1) mod n = front

```
def isEmpty():
	return front == rear
	
def isFull():
	return (rear+1) % len(cQ) == front
```

#### 삽입: enQueue(item)

- 마지막 원소 뒤에 새로운 원소를 삽입하기 위해

  - rear값을 조정하여 새로운 원소를 삽입할 자리를 마련함

    - rear <- (rear+1) mod n;

  - 그 인덱스에 해당하는 배열원소 cQ[rear]에 item을 저장

    ```
    def enQueue(item);
    	global rear
    	if isFull():
    		print("Queue_Full")		#디버깅용
    	else:
    		rear = (rear+1)%len(cQ)
    		cQ[rear] = item
    ```

#### 삭제: deQueue(), delete()

- 가장 앞에 있는 원소를 삭제하기 위해

  - front 값을 조정하여 삭제할 자리를 준비함
  - 새로운 front 원소를 리턴 함으로써 삭제와 동일한 기능함

  ```
  def deQueue():
  	global front
  	if isEmpty():
  		print("Queue_Empty")
  	else:
  		front = (front+1) % len(cQ)
  		return cQ[front]
  
  def delete():
  	global front
  	if isEmpty():
  		print("Queue_Empty")
  	else:
  		front = (front+1) % len(cQ)
  ```

  

## 연결큐

### 구조

- 단순 연결 리스트(Linked List)를 이용한 큐
  - 큐의 원소: 단순 연결 리스트의 노드
  - 큐의 원소 순서: 노드의 연결 순서, 링크로 연결되어 있음
  - front: 첫 번째 노드를 가리키는 링크
  - rear: 마지막 노드를 가리키는 링크
- 상태 표현
  - 초기 상태: front = rear = null
  - 공백 상태: front = rear = null
- 예

| 0x1000 |        |      | 0x1008 |        |      | 0x1010 |        |      | 0x1018 |      |
| ------ | ------ | ---- | ------ | ------ | ---- | ------ | ------ | ---- | ------ | ---- |
| A      | 0x1008 | →    | B      | 0x1010 | →    | C      | 0x1018 | →    | D      | NULL |
| front  |        |      |        |        |      |        |        |      | rear   |      |

### 구현 예(Python)

```python
class Node:
    def __init__(self, item, n=None):
        self.item = item
        self.next = n
        
def enQueue(item): 		#연결 큐의 삽입 연산
    global front, rear
    newNode = Node(item)	# 새로운 노드 생성
    if front == None: 		# 큐가 비어있다면
        fornt = newNode
    else:
        rear.next = newNode
    rear = newNode

def isEmpty():
    return front == None

def deQueue():		# 연결 큐의 삭제 연산
    global front, rear
    if isEmpty():
        print("Queue_Empty")
        return None
    
    item = front.item
    front = front.next
    if front == None:
        rear = None
    return item

def Qpeek():
    return front.item

def printQ():
    f = front
    s = ''
    while f:
        s += f.item + ''
        f = f.next
    return s
```



## 우선순위 큐(Priority Queue)

- 특성
  - 우선순위를 가진 항목들을 저장하는 큐
  - FIFO 순서가 아니라 우선순위가 높은 순서대로 먼저 나가게 된다.
- 적용 분야
  - 시뮬레이션 시스템
  - 네트워크 트래픽 제어
  - 운영체제의 테스크 스케줄링
- 구현
  - 배열을 이용한 우선순위 큐
  - (연결)리스트를 이용한 우선순위 큐
- 기본연산
  - 삽입: enQueue
  - 삭제: deQueue

### 배열을 이용한 우선순위 큐

- 구현
  - 배열을 이용하여 자료 저장
  - 원소를 삽입하는 과정에서 우선순위를 비교하여 적절한 위치에 삽입하는 구조
  - 가장 앞에 최고 우선순우의 원소가 위치하게 됨
- 문제점
  - 배열을 사용하므로, 삽입이나 삭제 연산이 일어날 때 원소의 재배치가 발생함
  - 이에 소요되는 시간이나 메모리 낭비가 큼



## 큐의 활용: 버퍼(Buffer)

- 버퍼
  - 데이터를 한 곳에서 다른 한 곳으로 전송하는 동안 일시적으로 그 데이터를 보관하는 메모리의 영역
  - 버퍼링: 버퍼를 활용하는 방식 또는 버퍼를 채우는 동작을 의미한다.
- 버퍼의 자료구조
  - 버퍼는 일반적으로 입출력 및 네트워크와 관련된 기능에서 이용된다.
  - 순서대로 입력/출력/전달되어야 하므로 FIFO 방식의 자료구조인 큐가 활용된다.

#### 키보드 버퍼

- 수행 과정
  - 사용자 키보드 입력
  - 키보드 입력 버퍼
  - 키보드 입력 버퍼에 Enter 키 입력이 들어오면
  - 프로그램 실행(연산)



## Revisit to 마이쮸

### Queue를 이용하여 마이쮸 나눠주기 시뮬레이션 해보기

1번이 줄은 선다.

1번이 한 개의 마이쮸를 받는다.



1번이 다시 줄을 선다.

새로 2번이 들어와 줄을 선다.



1번이 두 개의 마이쮸를 받는다.

1번이 다시 줄을 선다.

새로 3번이 들어와 줄을 선다.



2번이 한개의 마이쮸를 받는다.

2번이 다시 줄을 선다.

새로 4번이 들어와 줄을 선다.



1번이 세 개의 마이쮸를 받는다.

1번이 다시 줄을 선다

새로 5번이 들어와 줄을 선다.



3번이 한 개의 마이쮸를 받는다.



...



20개의 마이쮸가 있을 때 마지막 것을 누가 가져갈까?



20개

​	1번 1개

19개

​	1번 2개

​	1번 2개, 2번 1개

17개

​	2번 1개

​	2번 1개	1번 3개

​	2번 1개	1번 3개	3번 1개

16개

​	1번 3개	3번 1개

​	1번 3개	3번 1개	2번 2개

​	1번 3개	3번 1개	2번 2개	4번 1개

13개

​	3번 1개	2번 2개	4번 1개

​	3번 1개	2번 2개	4번 1개	1번 4개

​	3번 1개	2번 2개	4번 1개	1번 4개	5번 1개

12개

​	2번 2개	4번 1개	1번 4개	5번 1개

...

결과는??



#### 마이쮸 시뮬레이션 구현

엔터를 칠 때마다 다음 정보를 화면에 출력해 보자.

- 큐에 있는 사람 수
- 현재 일인당 나눠주는 사탕의 수
- 현재까지 나눠준 사탕의 수







## BFS(Breadth First Search)

- 그래프를 탐색하는 방법에는 크게 두 가지가 있음
  - 깊이 우선 탐색(Depth First Search, DFS)
  - 너비 우선 탐색(Breadth First Search, BFS)
- 너비 우선 탐색은
  - 탐색 시작점의 인접한 정점들을 먼저 모두 차례로 방문한 후<br> 방문했던 정점을 시작점으로 하여 다시 인접한 정점들을 차례로 방문하는 방식
- 인접한 정점들에 대해 탐색을 한 후
  - 차례로 다시 너비우선탐색을 진행해야 하므로,
  - 선입선출 형태의 자료구조인 큐를 활용함



### BFS 알고리즘

- 입력 파라미터: 그래프 G와 탐색 시작점v

  ```
  def BFS(G, v):		#그래프 G, 탐색 시작점v
  	visited = [0]*(n+1)			# 방문표시 배열 생성(n: 정점의 개수)
  	queue = []					# 큐 생성
  	queue.append(v)             # 시작점 v를 큐에 삽입 enQueue
  	while queue:				# 큐가 비어있지 않은 경우
  		t = queue.pop(0)		# 큐의 첫번째 원소 반환
  		if not visited[t]		# 방문되지 않은 곳이라면
  			visited[t] = True	#방문한 것으로 표시
  			do(t)				# 정점 t에서 할 일
              for i in G[t]:			# t와 연결된 모든 정점에 대해
                  if not visited[i]:	# 방문되지 않은 곳이라면
                      queue.append(i)	# 큐에 넣기
  ```

  

#### 예제



```
       A
  B    C    D
E   F   G   H   I
A-B, A-C, A-D
B-E, B-F, D-G, D-H, D-I

# 탐색 순서
A, B, C, D, E, F, G, H, I
```

- 초기상태

  - visited 배열 초기화
  - Q 생성
  - 시작점 enqueue

  ```
  visited = [F, F, F, F, F, F, F, F, F]
  Q = [A]
  ```

- A 점부터 시작

  - dequeue A
  - A 방문한 것으로 표시
  - A의 인접점 enqueue(인접점은 인접행렬이나 리스트로 구함)

  ```
  visited = [T, F, F, F, F, F, F, F, F]
  Q = [B, C, D]
  ```

- 탐색 진행

  - dequeue B
  - B 방문한 것으로 표시
  - B의 인접점 enqueue

  ```
  visited = [T, T, F, F, F, F, F, F, F]
  Q = [C, D, E, F]
  ```

- 탐색 진행

  - dequeue C
  - C 방문한 것으로 표시
  - C의 인접점 enqueue

  ```
  visited = [T, T, T, F, F, F, F, F, F]
  Q = [D, E, F]
  ```

- 탐색 진행

  - dequeue D
  - D 방문한 것으로 표시
  - D의 인접점 enqueue

  ```
  visited = [T, T, T, T, F, F, F, F, F]
  Q = [E, F, G, H, I]
  ```

- E, F, G, H, I 순으로 탐색 진행(인접점이 없으므로 enqueue없음)

- Q가 비면 탐색 종료

  ```
  visited = [T, T, T, T, T, T, T, T, T]
  Q = []
  ```

- 즉, 큐가 비어있지 않으면 반복



#### 예제2

```
       A
  B    C    D
E   F   G   H   I
A-B, A-C, A-D
B-C
B-E, B-F, D-G, D-H, D-I

# 탐색 순서
A, B, C, D, E, F, G, H, I
```

- A
- A 확인
  - A인접 enQ: BCD
    - B 확인
    - B인접 enQ: BCCEF
    - C처럼 연결이 여러 개인 경우 여러번 추가 될 수 있다.<br>(visited 전에 A인접과 B인접 추가로 두 번 추가 됨)

```
while Q:							
	v = deQ()						# 꺼내기
	do(v)							# 정점v에 대해 할일 하기
	if v에 인접 and 미방문인 모든 w:
		enQ(w)
		visited(w) = 1				# 방문 확인
```

- 위처럼 하면 C가 중복 안됨



#### 정점까지의 최단 거리를 알고 싶을 때

```
def BFS(G, v, n):		#그래프 G, 탐색 시작점v
	visited = [0]*(n+1)			# 방문표시 배열 생성(n: 정점의 개수)
	queue = []					# 큐 생성
	queue.append(v)             # 시작점 v를 큐에 삽입 enQueue
	visited[v] = 1
	while queue:				# 큐가 비어있지 않은 경우
		t = queue.pop(0)		# 큐의 첫번째 원소 반환
		do(t)					# 정점 t에서 할일
		for i in G[t]:			# t와 연결된 모든 정점에서
			if not visited[i]	# 방문되지 않은 곳이면
				queue.append(i)	# 큐에 넣기
				visited[i] = visited[t] + 1		
				#출발 정점으로부터의 거리를 알 수 있게 됨
				
# visited에 거리정보가 저장됨
visited = [1, 2, 2, 2, 3, 3, 3, 3, 3]
```





#### 연습문제

- 다음은 연결되어 있는 두 개의 정점 사이의 간선을 순서대로 나열 해 놓은 것이다. 모든 정점을 너비우선탐색하여 경로를 출력하시오.(간선 방향 없음)
  - 시작 정점은 1
  - 1, 2, 1, 3, 2, 4, 2, 5, 4, 6, 5, 6, 6, 7, 3, 7
  - 출력 결과: 1 2 3 4 5 **7** 6

````python
```
7 8
1 2 1 3 2 4 2 5 4 6 5 6 6 7 3 7
```

def bfs(s, V):		# 인접 행렬 이용
    q = []		# 큐 생성
    visited = [0]*(V+1)	# visited 생성
    q.append(s)			# 시작점 인큐
    visited[s] = 1		# 시작점 visited 표시
    while q:			# 큐가 비어있지 않으면 (처리할 정점이 남아 있지 않으면)
        t = q.pop(0)    # 디큐(꺼내서)해서 t에 저장
        print(t)		# t에 대한 처리
        for i in range(1, V+1):		# t에 인접이고 미방문인 모든 i에 대해
            if adj[t][i] == 1 and visited[i] == 0:
                q.append(i)		# enqueue(i)
                visited[i] = visited[t] + 1		# i에 visited로 표시
                
def bfs2(s, V):		# 인접 리스트 이용
    q = []		# 큐 생성
    visited = [0]*(V+1)	# visited 생성
    q.append(s)			# 시작점 인큐
    visited[s] = 1		# 시작점 visited 표시
    while q:			# 큐가 비어있지 않으면 (처리할 정점이 남아 있지 않으면)
        t = q.pop(0)    # 디큐(꺼내서)해서 t에 저장
        print(t)		# t에 대한 처리
        for i in adjList[t]:		# t에 인접이고 미방문인 모든 i에 대해
            if visited[i] == 0:
                q.append(i)		# enqueue(i)
                visited[i] = visited[t] + 1		# i에 visited로 표시
    
V, E = map(int, input().split())
edge = list(map(int, input().split()))
adj = [[0]*(V+1) for _ in range(V+1)]			# 인접행렬
#adjList = [[] for _ in range(v+1)]				# 인접리스트
for i in range(E):
    n1, n2 = edge[2*i], edge[2*i+1]
    adj[n1][n2] = 1
    #adj[n2][n1] = 1						# 방향이 없는 그래프인 경우 추가
    
    #adjList[n1].append(n2)					# 인접리스트 만들기
    #adjList[n2].append(n1)
    
bfs(1, V)
bfs2(1, v)
````



````python
```
7 8
1 2 1 3 2 4 2 5 4 6 5 6 6 7 3 7
```

def bfs3(s, V):			# front, rear 활용
    q = [0]*V				# 큐 생성
    front = -1
    rear = -1				
    visited = [0]*(V+1)		# visited 생성
    rear += 1
    q[rear] = s
    visited[s] = 1 			# 시작점 visited
    while front != rear:	# 큐가 비어있지 않으면
        front += 1
        t = q[front]
        print(t)
        for i in range(1, V+1):		# t에 인접하고 미방문인 모든 i에 대해
            if adj[t][i] == 1 and visited[i] == 0:
                rear += 1			# 인큐 i
                q[rear] = i
                visited[i] = visited[t] + 1		# i 방문 표시
    
V, E = map(int, input().split())
edge = list(map(int, input().split()))
adj = [[0]*(V+1) for _ in range(V+1)]			# 인접행렬
#adjList = [[] for _ in range(v+1)]				# 인접리스트
for i in range(E):
    n1, n2 = edge[2*i], edge[2*i+1]
    adj[n1][n2] = 1
    #adj[n2][n1] = 1						# 방향이 없는 그래프인 경우 추가
    
    #adjList[n1].append(n2)					# 인접리스트 만들기
    #adjList[n2].append(n1)
    
bfs3(1, V)
````

