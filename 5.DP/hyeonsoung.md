## 11726. 2×n 타일링
https://www.acmicpc.net/problem/11726

### 코드

```java
import java.util.Scanner;

public class Sol11726 {

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);

		int n = sc.nextInt();
		
		long [] arr = new long[1001];
		
		arr[1] = 1;
		arr[2] = 2;
		int mod = 10007;
		for(int i = 3; i <= n; i++) {
			arr[i] = (arr[i - 1] + arr[i - 2]) % mod;
		}
		System.out.println(arr[n]);
	}
}
```

## 11727. 2×n 타일링 2
https://www.acmicpc.net/problem/11727

### 코드

```java
import java.util.Scanner;

public class Sol11727 {

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		long[] arr = new long[1001];
		int mod = 10007;
		arr[1] = 1;
		arr[2] = 3;
		for(int i = 3; i <= n; i++) {
			
			arr[i] = (arr[i - 1] + (arr[i - 2] * 2)) % mod;
		}
		System.out.println(arr[n]);
	}
}
```

## 1463. 1로 만들기
https://www.acmicpc.net/problem/1463

### 코드

```java
import java.util.Scanner;

public class Sol1463 {

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int [] arr = new int[n + 1];
		arr[1] = 0;
		
		for(int i = 2; i <= n; i++) {
			arr[i] = arr[i - 1] + 1;
			if(i % 2 == 0) {
				arr[i] = Math.min(arr[i], arr[i / 2] + 1);
			}
			if(i % 3 == 0) {
				arr[i] = Math.min(arr[i], arr[i / 3] + 1);
			}
		}
		System.out.println(arr[n]);
	}
}
```
