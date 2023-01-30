## 문제
[https://www.acmicpc.net/problem/8393
](https://www.acmicpc.net/problem/8393)

n이 주어졌을 때, 1부터 n까지 합을 구하는 프로그램을 작성하시오.

### 입력
첫째 줄에 n (1 ≤ n ≤ 10,000)이 주어진다.
```
3
```
### 출력
첫째 줄에 갑옷을 만들 수 있는 개수를 출력한다.

```
6
```
## 풀이



### 코드

```java
import java.util.Scanner;

public class Sum {
  public static void main(String[] args) {
    Scanner sc = new Scanner(System.in);
    int n = sc.nextInt();
    int sum = 0;
    for(int i = 1; i <= n; i++) {
      sum += i;
    }
    System.out.println(sum);
  }
}

```
