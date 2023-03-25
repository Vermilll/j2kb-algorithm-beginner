# 9주차

이분 탐색과 분할정복 이론 공부

분할정복: 백준 2630, 2448, 1780, 1992
이분 탐색: 백준 2512, 2110, 2470

이론공부

---

**이분 탐색(이진 탐색) 알고리즘:**

정렬되어 있는 리스트에서 탐색 범위를 절반씩 좁혀가며 데이터를 탐색하는 방법.

- 이진 탐색은 배열 내부의 데이터가 정렬되어 있어야만 사용할 수 있는 알고리즘
- 변수 3개(start, end, mid)를 사용하여 탐색.
- 찾으려는 데이터와 중간점 위치에 있는 데이터를 반복적으로 비교해서 원하는 데이터를 찾는 것이 이진탐색의 과정.

참고문헌: [https://velog.io/@kimdukbae/이분-탐색-이진-탐색-Binary-Search](https://velog.io/@kimdukbae/%EC%9D%B4%EB%B6%84-%ED%83%90%EC%83%89-%EC%9D%B4%EC%A7%84-%ED%83%90%EC%83%89-Binary-Search)

**분할 정보 알고리즘**

분할 정복: 가장 유명한 알고리즘으로 둘 이상의 부분 문제로 나눈 뒤 각 문제에 대한 답을 재귀 호출을 이용해 계산하고, 각 부분 문제의 답으로부터 전체 문제의 답을 계산

- 분할 정복이 일반 재귀 호출과 다른 점은 문제를 한 조각과 나머지 전체로 나누는 대신 거의 같은 크기의 부분 문제로 나누는 것.

문제풀이

---

## 2630. 색종이 만들기

[https://www.acmicpc.net/problem/2630](https://www.acmicpc.net/problem/2630)

### 코드

```python
import sys
input = sys.stdin.readline
n = int(input())
B = [list(map(int, input().split())) for _ in range(n)]
w_cnt, b_cnt = 0, 0

def div_conq(x, y, N):
    global w_cnt, b_cnt
    tmp_cnt = 0
    for i in range(x, x + N):
        for j in range(y, y + N):
            if B[i][j]:
                tmp_cnt += 1
    if not tmp_cnt:
        w_cnt += 1
    elif tmp_cnt == N**2:
        b_cnt += 1
    else:
        div_conq(x, y, N // 2)
        div_conq(x + N // 2, y, N // 2)
        div_conq(x, y + N // 2, N // 2)
        div_conq(x + N // 2, y + N // 2, N // 2)
    return

div_conq(0, 0, n)
print(w_cnt)
print(b_cnt)
```