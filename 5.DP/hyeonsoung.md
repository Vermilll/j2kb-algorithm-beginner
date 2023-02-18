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