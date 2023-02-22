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

## 9095. 1, 2, 3 더하기
https://www.acmicpc.net/problem/9095

### 코드

```java
import java.util.Scanner;

//0 = 0, 1 = 1, 2= 2, 3= 4, 4= 7, 5= 14
// 4는 1 + 3 이다. 3을 1, 2, 3 더하기로 하였을 때의 경우의 수는 4가지이다.
// 4는 2 + 2이다. 2를 1, 2, 3 더하기로 하였을 때의 경우의 수는 2가지이다.
// 4는 3 + 1이다. 1을 1, 2, 3 더하기로 하였을 때의 경우의 수는 1가지이다.
// 5는 1 + 4이다. 4를 1, 2, 3 더하기로 하였을 때의 경우의 수는 7가지이다.
// 5는 2 + 3이다. 3를 1, 2, 3 더하기로 하였을 때의 경우의 수는 4가지이다.
// 5는 3 + 2이다. 2을 1, 2, 3 더하기로 하였을 때의 경우의 수는 2가지이다.

public class Sol9095 {

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		int n = sc.nextInt();
		
		int [] arr = new int[11];
		arr[0] = 0;
		arr[1] = 1;
		arr[2] = 2;
		arr[3] = 4;
		for(int i = 0; i < n; i++) {
			int ex = sc.nextInt();
			for(int j = 4; j <= ex; j++) {
				arr[j] = arr[j - 1] + arr[j - 2] + arr[j - 3];
			}
			System.out.println(arr[ex]);
		}
	}
}
```
