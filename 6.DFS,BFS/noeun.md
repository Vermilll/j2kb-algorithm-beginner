## 2026 번

```java

public class b2606 {
  public static void main(String[] args) throws IOException {
    
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    int cnt = Integer.parseInt(br.readLine());
    int connect = Integer.parseInt(br.readLine());
    StringTokenizer st;
    Queue<Integer> que = new LinkedList<>();
    
    int[][] arr = new int[cnt+1][cnt+1];
    
    for(int i=0; i<connect; i++) {
      st = new StringTokenizer(br.readLine());
      int x = Integer.parseInt(st.nextToken());
      int y = Integer.parseInt(st.nextToken());
      
      arr[x][y] = 1;
      arr[y][x] = 1;
    }
    
    boolean[] visited = new boolean[cnt+1];
    visited[1] = true;
    que.add(1);
    int result = 0;
    
    while(!que.isEmpty()) {
      int now = que.poll();
      for(int i=1; i<=cnt; i++) {
        if(arr[now][i] ==1 && !visited[i]) {
          que.add(i);
          visited[i] = true;
          result++;
        }
      }
    }
    
    System.out.println(result);
    
    br.close();
    
  }
}


```

<br/>

## 11724 번

```java

public class b11724 {
  public static void main(String[] args) throws IOException {
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    StringTokenizer st = new StringTokenizer(br.readLine());
    
    int N = Integer.parseInt(st.nextToken());
    int M = Integer.parseInt(st.nextToken());
    int[][] arr = new int[N+1][N+1];
    boolean[] visited = new boolean[N+1];
    Queue<Integer> que = new LinkedList<>();
    int result = 0;
    
    for(int i=0; i<M; i++) {
      st = new StringTokenizer(br.readLine());
      int x = Integer.parseInt(st.nextToken());
      int y = Integer.parseInt(st.nextToken());
      arr[x][y] = 1;
      arr[y][x] = 1;
    }
    
    for(int i=1; i<=N; i++) {
      if(!visited[i]) {
        visited[i] = true;
        que.add(i);
        result++;
      }
      
      while(!que.isEmpty()) {
        int now = que.poll();
        for(int j=1; j<=N; j++) {
          if(arr[now][j] == 1 && !visited[j]) {
            que.add(j);
            visited[j] = true;
          }
        }
      }
    }
    
    System.out.println(result);
    br.close();
    
  }
}


```

<br/>

## 10451 번

```java

public class b10451 {
  public static void main(String[] args) throws IOException {
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    int T = Integer.parseInt(br.readLine());
    StringTokenizer st;
    Queue<Integer> que = new LinkedList<>(); 
    int result = 0;
    
    for(int i=0; i<T; i++) {
      int N = Integer.parseInt(br.readLine());
      st = new StringTokenizer(br.readLine());
      result = 0;
      que.clear();
      int[][] arr = new int[N+1][N+1];
      boolean[] visited = new boolean[N+1];
      
      for(int j=1; j<=N; j++) {
        int next = Integer.parseInt(st.nextToken());
        arr[j][next] = 1; 
      }
      
      for(int j=1; j<=N; j++) {
        if(!visited[j]) {
          visited[j] = true;
          que.add(j);
          result++;
        }
        
        while(!que.isEmpty()) {
          int now = que.poll();
          for(int k=1; k<=N; k++) {
            if(arr[now][k]==1 && !visited[k]) {
              visited[k] = true;
              que.add(k);
            }
          }
        }
        
      }
    
      System.out.println(result);
    }
    
    br.close();
  }
}


```

<br/>

## 1012 번

```java

public class b2606 {
  public static void main(String[] args) throws IOException {
    
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    int cnt = Integer.parseInt(br.readLine());
    int connect = Integer.parseInt(br.readLine());
    StringTokenizer st;
    Queue<Integer> que = new LinkedList<>();
    
    int[][] arr = new int[cnt+1][cnt+1];
    
    for(int i=0; i<connect; i++) {
      st = new StringTokenizer(br.readLine());
      int x = Integer.parseInt(st.nextToken());
      int y = Integer.parseInt(st.nextToken());
      
      arr[x][y] = 1;
      arr[y][x] = 1;
    }
    
    boolean[] visited = new boolean[cnt+1];
    visited[1] = true;
    que.add(1);
    int result = 0;
    
    while(!que.isEmpty()) {
      int now = que.poll();
      for(int i=1; i<=cnt; i++) {
        if(arr[now][i] ==1 && !visited[i]) {
          que.add(i);
          visited[i] = true;
          result++;
        }
      }
    }
    
    System.out.println(result);
    
    br.close();
    
  }
}


```



