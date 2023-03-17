# 8주차

그리디 알고리즘 공부

**그리디 알고리즘**

---

- 그리디 알고리즘(탐욕법)은 현재 상황에서 지금 당장 좋은 것만 고르는 방법을 의미한다.
- 일반적인 그리디 알고리즘은 문제를 풀기 위한 최소한의 아이디어를 떠올릴 수 있는 능력을 요구한다.
- 그리디 해법은 그 정당성 분석이 중요하다.
- 단순히 가장 좋아보이는 것을 반복적으로 선택해도 최적의 해를 구할 수 있는지 검토한다.

개념 설명 출처: [https://velog.io/@kyunghwan1207/그리디-알고리즘Greedy-Algorithm-탐욕법](https://velog.io/@kyunghwan1207/%EA%B7%B8%EB%A6%AC%EB%94%94-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98Greedy-Algorithm-%ED%83%90%EC%9A%95%EB%B2%95)

**문제풀이**

---

## 1783. 병든 나이트

[https://www.acmicpc.net/problem/1783](https://www.acmicpc.net/problem/1783)

### 코드

```python
from sys import stdin

Y, X = map(int, stdin.readline().split())

if Y == 1:
    print(1)
elif Y == 2:
    print(min(4, (X + 1) // 2))
else:
    if X <= 6:
        print(min(4, X))
    else:
        print(X-2)
```