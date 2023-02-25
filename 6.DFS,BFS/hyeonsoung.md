## 2606. 바이러스
https://www.acmicpc.net/problem/2606

### 코드

```java
import java.util.ArrayList;
import java.util.Scanner;

public class Sol2606 {
	static int v;
	static int cnt = 0;
	static boolean[] visited;
	static ArrayList<Integer> arr[];
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
		int n = sc.nextInt();
		int m = sc.nextInt();
		v = 1;
		
		visited = new boolean[n + 1];
		arr = new ArrayList[n + 1];
		
		for(int i = 1; i <= n; i++) {
			arr[i] = new ArrayList<>();
		}
		
		for(int i = 0; i < m; i++) {
			int x = sc.nextInt();
			int y = sc.nextInt();
			arr[x].add(y);
			arr[y].add(x);
		}
		System.out.println(DFS(v));
	}

	private static int DFS(int i) {
		visited[i] = true;
		for(int b : arr[i]) {
			if(visited[b] == false) {
				cnt++;
				DFS(b);
			}
		}
		return cnt;
	}
}
```
