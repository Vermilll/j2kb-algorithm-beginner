## 10870. 피보나치 수 5
https://www.acmicpc.net/problem/10870

### 코드

```java
import java.util.Scanner;

public class Sol10870 {

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		
		int [] arr = new int[n + 1];
		
		for(int i = 0; i <= n; i++) {
			if(i == 0) {
				arr[i] = 0;
			}
			else if(i == 1) {
				arr[i] = 1;
			}
			else {
				arr[i] = arr[i - 1] + arr[i - 2];
			}
		}
		System.out.println(arr[n]);
	}
}
```

## 2750. 수 정렬하기
https://www.acmicpc.net/problem/2750

### 코드

```java
import java.util.Arrays;
import java.util.Scanner;

public class Sol2750 {

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int [] arr = new int [n];
		for(int i = 0; i < n; i++) {
			arr[i] = sc.nextInt();
		}
		Arrays.sort(arr);
		for(int i = 0; i < n; i++) {
			System.out.println(arr[i]);
		}
	}
}

```
