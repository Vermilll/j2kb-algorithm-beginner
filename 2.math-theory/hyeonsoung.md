## 8393. 합
[https://www.acmicpc.net/problem/8393
](https://www.acmicpc.net/problem/8393)

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

## 1929. 소수 구하기
https://www.acmicpc.net/problem/1929

### 에라토스테네스 개념
1. 구하고자 하는 소수의 범위만큼 1차원 배열을 생성
2. 2부터 시작하고 현재 숫자가 지워지지 않을 때는 현재 선택된 숫자의 배수에 해당하는 수를 배열에서 끝까지 탐색하면서 지운다. 이때 처음으로 선택된 수는 지우지 않는다.
또한 2부터 N의 제곱근까지 값을 탐색한다. 값이 인덱스 값이면 그대로 두고 그 값의 배수를 탐색해 지운다. 
3. 배열의 끝까지 2번을 반복한 후 배열에서 남아있는 모든 수를 출력한다.

N의 제곱근까지만 탐색하는 이유
>N이 a * b라고 가정했을 때, a와 b 모두 N의 제곱근 보다 클 수 없다. 따라서 N의 제곱근까지만 확인해도 전체 범위의 소수를 확인할 수 있다. 만약 16의 범위까지의
>소수를 구할 때 16=4 * 4로 이뤄지면 16보다 작은 숫자는 항상 4보다 작은 약수를 갖게 된다는 뜻이다

https://www.youtube.com/watch?v=R1vl8FNAC6Q&list=PLFgS-xIWwNVX-zm4m6suWC9d7Ua9z7fuT&index=24

### 코드

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.StringTokenizer;

public class Sosu {

	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		int start = Integer.parseInt(st.nextToken());
		int end = Integer.parseInt(st.nextToken());
		
		int [] arr = new int[end + 1];
		for(int i = 1; i <= end; i++) {
			arr[i] = i;
		}
		for(int i = 2; i <= Math.sqrt(end); i++) {
			// 소수가 아닌것 
			if(arr[i] == 0) {
				continue;
			}
			for(int j = i + i; j <= end; j = j + i) {
				arr[j] = 0;
			}
		}
		for(int i = start; i <= end; i++) {
			 if (arr[i] != 0 && i != 1) {
				System.out.println(arr[i]);
			}
		}
		
	}
}
```

## 1978. 소수 찾기
[https://www.acmicpc.net/problem/1978](https://www.acmicpc.net/problem/1978)

### 코드

```java
import java.util.Scanner;

public class SosuSearch {

	public static void main(String[] args) {
		// Input
		Scanner sc = new Scanner(System.in);
		int n  = sc.nextInt();
		int[] arr = new int[n];
		for(int i = 0 ; i < n; i++) {
			arr[i] = sc.nextInt();
		}
		int cnt = 0;
		
		// Output
		for(int i = 0; i < n; i++) {
			boolean isPrime = false;
			if(arr[i] == 1) {
				continue;
			}
			for(int j = 2; j < arr[i]; j++) {
				if(arr[i] % j == 0) {
					isPrime = true;
					break;
				}
			}
			if(!isPrime) {
				cnt++;
			}
		}
		System.out.println(cnt);
	}
}
```
