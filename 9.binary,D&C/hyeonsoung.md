## 2512. 예산
https://www.acmicpc.net/problem/2512

### 코드

```java
import java.util.Arrays;
import java.util.Scanner;

public class Sol2512 {

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		int n = sc.nextInt();
		
		int [] arr = new int[n];
		
		for(int i = 0; i < n; i++) {
			arr[i] = sc.nextInt();
		}
		Arrays.sort(arr);
		Long m = sc.nextLong();
		
		long lt = 0;
		long rt = arr[n - 1];
		long answer = 0;
		
		while(lt <= rt) {
			long mid = (lt + rt) / 2;
			long sum = 0;
			
			for(int i = 0; i < n; i++) {
				int money = arr[i];
				if(money >= mid) {
					sum += mid;
				}
				else {
					sum += money;
				}
			}
			
			if(sum > m) {
				rt = mid - 1;
			}
			else {
				lt = mid + 1;
				answer = Math.max(answer, mid);
			}
		}
		System.out.println(answer);	
	}
}
```
