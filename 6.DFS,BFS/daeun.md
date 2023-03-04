# 6주차

DFS / BFS 이론 공부

**DFS - 깊이 우선 탐색 (Depth-First Search)**

---

루트 노드(혹은 다른 임의의 노드)에서 시작해서 다음 분기로 넘어가기 전에 해당 분기를 완벽하게 탐색하는 방식을 말한다.

1. 모든 노드를 방문하고자 하는 경우에 이 방법을 선택
2. 깊이 우선 탐색(DFS)이 너비 우선 탐색(BFS)보다 좀 더 간단
3. 검색 속도 자체는 너비 우선 탐색(BFS)에 비해서 느림

**BFS - 너비 우선 탐색(Breadth-First Search)**

---

루트 노드(혹은 다른 임의의 노드)에서 시작해서 인접한 노드를 먼저 탐색하는 방법으로, 

시작 정점으로부터 가까운 정점을 먼저 방문하고 멀리 떨어져 있는 정점을 나중에 방문하는 순회 방법이다.

주로 두 노드 사이의 최단 경로를 찾고 싶을 때 이 방법을 선택한다.

|                                            DFS |                                          BFS |
| --- | --- |
| 현재 정점에서 갈 수 있는 점들까지 들어가면서 탐색. | 현재 정점에서 연결된 가까운 점들부터 탐색  |
| 스틱 또는 재귀함수로 구현 | 큐를 이용해서 구현 |

참고문헌: [https://velog.io/@lucky-korma/DFS-BFS의-설명-차이점](https://velog.io/@lucky-korma/DFS-BFS%EC%9D%98-%EC%84%A4%EB%AA%85-%EC%B0%A8%EC%9D%B4%EC%A0%90)

---

## 1260. DFS와 BFS

[https://www.acmicpc.net/problem/1260](https://www.acmicpc.net/problem/1260)

### 코드

```python
n, m, v = map(int, input().split())
# 행 열 번호를 사용하기위해 0번째 인덱스 0으로 초기화
s = [[0] * (n + 1) for i in range(n + 1)]
# 방문 체크 리스트
visit = [0 for i in range(n + 1)]
for i in range(m):
    x, y = map(int, input().split())
    s[x][y] = 1
    s[y][x] = 1

def dfs(v):
    print(v, end=' ')
    # 방문 노드 체크
    visit[v] = 1
    for i in range(1, n + 1):
    	# 방문한적 없는 인접 노드 방문
        if visit[i] == 0 and s[v][i] == 1:
            dfs(i)

def bfs(v):
	# 시작 노드 큐에 추가
    queue = [v]
    # 방문 노드 체크
    visit[v] = 0
    # 큐가 빌때까지 반복
    while (queue):
    	# 시작 노드 추출
        v = queue[0]
        print(v, end=' ')
        # 시작 노드 제거
        del queue[0]
        for i in range(1, n + 1):
        	# 방문한적 없는 인접 노드 방문
            if visit[i] == 1 and s[v][i] == 1:
                queue.append(i)
                visit[i] = 0

dfs(v)
print()
bfs(v)
```

## 11724. 연결 요소의 개수

[https://www.acmicpc.net/problem/11724](https://www.acmicpc.net/problem/11724)

### 코드

DFS로 문제풀이

```python
import sys

sys.setrecursionlimit(5000)
input = sys.stdin.readline

# dfs로 그래프를 탐색한다.
def dfs(start, depth):

    #해당 노드 방문체크 한다.
    visited[start] = True

    # 해당 시작점을 기준으로 계속해서 dfs로 그래프를탐색한다.
    for i in graph[start]:
        if not visited[i]:
            dfs(i, depth + 1)

N, M = map(int, input().split())
graph = [[] for _ in range(N + 1)]

for _ in range(M):
    a, b = map(int, input().split())
    graph[a].append(b)
    graph[b].append(a)

# 방문처리
visited = [False] * (1 + N)
count = 0  # 컴포넌트 그래프 개수 저장

# 1~N번 노드를 각각돌면서
for i in range(1, N + 1):
    if not visited[i]:  # 만약 i번째 노드를 방문하지 않았다면
        if not graph[i]:  # 만약 해당 정점이 연결된 그래프가 없다면
            count += 1  # 개수를 + 1
            visited[i] = True  # 방문 처리
        else:  # 연결된 그래프가 있다면
            dfs(i, 0)  # dfs탐색을 돈다.
            count += 1  # 개수를 +1

print(count)
```

BFS로 문제풀이

```python
import sys
from collections import deque

input = sys.stdin.readline

def bfs(start):
    queue = deque([start])
    visited[start] = True
    while queue:
        node = queue.popleft()
        for i in graph[node]:
            if not visited[i]:
                visited[i] = True
                queue.append(i)

N, M = map(int, input().split())
graph = [[] for _ in range(N + 1)]

for _ in range(M):
    a, b = map(int, input().split())
    graph[a].append(b)
    graph[b].append(a)

# 방문처리
visited = [False] * (1 + N)
count = 0  # 컴포넌트 그래프 개수 저장

# 1~N번 노드를 각각돌면서
for i in range(1, N + 1):
    if not visited[i]:  # 만약 방문하지 않았다면
        if not graph[i]:  # 만약 그래프가 비어있다면
            count += 1  # 개수 1개 추가
            visited[i] = True  # 방문 처리
        else:  # 만약 그래프가 비어있지 않다면(어느 점과 연결된 점이 있다면)
            bfs(i)  # 해당 i를 시작노드로 bfs를 돈다.
            count += 1  # 연결요소 를 +1개 해준다.

print(count)
```

## 10451. 순열 사이클

[https://www.acmicpc.net/problem/10451](https://www.acmicpc.net/problem/10451)

### 코드

```python
def dfs(now):
	i = graph[now]
	if not visited[i]:
		visited[i] = True
		dfs(i)

for _ in range(int(input())):
	n = int(input())
	graph = [0] + list(map(int,input().split()))
	visited = [False]*(n+1)
	result = 0

	for i in range(1,n+1):
		if not visited[i]:
			dfs(i)
			result+=1
	
	print(result)
```