## 2178. 미로 탐색
https://www.acmicpc.net/problem/2178

### 코드

```java
import java.io.BufferedReader;
import java.io.InputStreamReader;
import java.util.LinkedList;
import java.util.Queue;
import java.util.StringTokenizer;

public class Sol2178 {
	static int s, e;
	static boolean visited[][];
	static int [][] arr;
	static int[] dx = {1, 0, -1, 0};
	static int[] dy = {0, 1, 0, -1};
	public static void main(String[] args) throws Exception {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		
		s = Integer.parseInt(st.nextToken());
		e = Integer.parseInt(st.nextToken());
		
		arr = new int[s][e];
		visited = new boolean[s][e];
		
		for(int i = 0; i < s; i++) {
			st = new StringTokenizer(br.readLine());
			String line = st.nextToken();
			for(int j = 0; j < e; j++) {
				arr[i][j] = Integer.parseInt(line.substring(j, j + 1));
			}
		}
		BFS(0, 0);
		System.out.println(arr[s - 1][e - 1]);
	}

	private static void BFS(int i, int j) {
		Queue<int[]> que = new LinkedList<>();
		que.offer(new int[] {i, j});
		visited[i][j] = true;
		while(!que.isEmpty()) {
			int [] now = que.poll();
			for(int k = 0; k < 4; k++) {
				int x = now[0] + dx[k];
				int y = now[1] + dy[k];
				if(x >= 0 && x < s && y >= 0 && y < e) {
					if(arr[x][y] != 0 && !visited[x][y]) {
						visited[x][y] = true;
						arr[x][y] = arr[now[0]][now[1]] + 1;
						que.offer(new int[] {x, y});
					}
				}
			}
		}
		
	}
}
```

## 5014. 스타트링크
https://www.acmicpc.net/problem/5014

### 코드

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.util.LinkedList;
import java.util.Queue;
import java.util.StringTokenizer;

public class Sol5014 {
	static int f, s, g, u, d;
	static boolean[] visited;
	public static void main(String[] args) throws IOException {
		BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
		StringTokenizer st = new StringTokenizer(br.readLine());
		f = Integer.parseInt(st.nextToken());
		s = Integer.parseInt(st.nextToken());
		g = Integer.parseInt(st.nextToken());
		u = Integer.parseInt(st.nextToken());
		d = Integer.parseInt(st.nextToken());
		
		visited = new boolean[f + 1];
		int result = bfs();
		if(result < 0) {
			System.out.println("use the stairs");
		}
		else {
			System.out.println(result);
		}
	}
	private static int bfs() {
		Queue<Node> que = new LinkedList<>();
		que.offer(new Node(s, 0));
		visited[s] = true;
		while(!que.isEmpty()) {
			Node current = que.poll();
			if(current.x == g) {
				return current.cost;
			}
			if(current.x + u <= f && visited[current.x + u] == false) {
                que.offer(new Node(current.x + u, current.cost + 1));
                visited[current.x + u] = true;
            }
            if(current.x - d >= 1 && visited[current.x - d] == false) {
                que.offer(new Node(current.x - d, current.cost + 1));
                visited[current.x - d] = true;
            }
		}
		return -1;
	}
	public static class Node {
        int x;
        int cost;
        
        public Node(int x, int cost) {
            this.x = x;
            this.cost = cost;
        }
    }
}
```
