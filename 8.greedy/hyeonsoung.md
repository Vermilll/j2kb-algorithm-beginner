## 1783. 병든 나이트 

### 코드

```java
public class Sol1783 {

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int m = sc.nextInt();

        int cnt = 0;

        if (n == 1) { //세로칸이 1일경우 이동 불가
            cnt = 1;
        } else if (n == 2) {//세로칸이 2일경우 2,3번 방향으로만 이동 가능, 1~4번 전부 이동 불가능
            cnt = Math.min((m + 1) / 2, 4);
        } else {//세로칸이 3칸 이상일 경우
            if (m<  7){
                cnt = Math.min(m, 4);
            } else {
                cnt = m - 2;
            }
        }
        System.out.println(cnt);

	}

```
## 11501. 주식

### 코드

```java
import java.util.Scanner;

public class Sol11501 {

	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		
		int T = sc.nextInt();
		
		for(int i = 0; i < T; i++) {
			int n = sc.nextInt();
			
			int [] stock = new int[n + 1];
			
			long gain = 0;
			int max = 0;
			
			for(int j = 0; j < n; j++) {
				stock[j] = sc.nextInt();
			}
			for(int j = n - 1; j > -1; j--) {
				if(stock[j] > max) {
					max = stock[j];
				}
				else {
					gain += (max - stock[j]);
				}
			}
			System.out.println(gain);
		}
	}
}
```
