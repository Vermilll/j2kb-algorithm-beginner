# 5주차

DP 이론 공부

DP - Dynamic Programming(동적계획법)

---

큰 문제를 작은 문제로 나누어 푸는 문제.

방법: 모든 작은 문제들을 한번만 풀어야함. 정답을 구한 작은 문제를 어딘가에 메모해 두고 다시 큰 문제를 풀 때 똑같은 작은 문제가 나타나면 앞서 메모한 작은 문제의 결과값을 이용.

조건: 작은 문제가 반복해서 일어나는 경우. 같은 문제는 구할 때마다 정답이 같음.

참고 문헌: [https://galid1.tistory.com/507](https://galid1.tistory.com/507)

---

## 9095. 1,2,3 더하기

[https://www.acmicpc.net/problem/9095](https://www.acmicpc.net/problem/9095)

### 코드

```python
cache = [0]*11
cache[1]=1 # 1
cache[2]=2 # 1+1,2
cache[3]=4 # 1+1+1+1,1+3,3+1,2+2

for i in range(4,11):
cache[i]=cache[i-1]+cache[i-2]+cache[i-3]

T=int(input())
for _ in range(T):
n=int(input())
print(cache[n])
```

## 11727. 2Xn 타일링 2

 [https://www.acmicpc.net/problem/11727](https://www.acmicpc.net/problem/11727)

### 코드

```python
import sys
input = sys.stdin.readline

n = int(input())
dp = [0] * 1001

# 초기값 지정
dp[0] = 1
dp[1] = 1

# 점화식에 따른 경우의 수 계산
for i in range(2, n+1):
    dp[i] = dp[i-1] + 2 * dp[i-2]

print(dp[n]%10007)
```

## 11722. 가장 긴 감소하는 부분 수열

[https://www.acmicpc.net/problem/11722](https://www.acmicpc.net/problem/11722)

### 코드

```python
import sys  #이전의 최대 길이를 이용해야 하므로 dp를 이용
input = sys.stdin.readline

def BOJ11722() :
  n = int(input())
  l = list(map(int, input().split()))
  dp = [1 for _ in range(n)]
  
  for i in range(n) :
    for j in range(i) :
      if l[i] < l[j] :
        dp[i] = max(dp[i], dp[j] + 1)

  print(max(dp))

BOJ11722()
```

## 11052. 카드 구매하기

[https://www.acmicpc.net/problem/11052](https://www.acmicpc.net/problem/11052)

### 코드

```python
n = int(input())
p = list(map(int, input().split()))
p.insert(0,0)
dp = [0 for _ in range(n+1)]

for i in range(1, n+1):
    for j in range(1,i+1):
        dp[i] = max(dp[i], p[j] + dp[i-j])
print(dp[n])
```