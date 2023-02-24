
## 1003 번

```java
public class b1003 {
  
  
  public static void main(String[] args) throws IOException {
    
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    int T = Integer.parseInt(br.readLine());
    
    int[] fibo0 = new int[41];
    int[] fibo1 = new int[41];
    fibo0[0] = 1;
    fibo0[1] = 0;
    fibo1[0] = 0;
    fibo1[1] = 1;
    
    for(int i=0 ;i<T; i++ ) {
      
      int num = Integer.parseInt(br.readLine());
      for(int j=2; j<=num; j++) {
        fibo0[j] = fibo0[j-1] + fibo0[j-2];
        fibo1[j] = fibo1[j-1] + fibo1[j-2];
      }
      
      System.out.println(fibo0[num] + " " + fibo1[num]);
    
    }
    
  }
  
}


```

<br/><br/>

## 9461 번

```java
public class b9461 {
  public static void main(String[] args) throws IOException {
    
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    int T = Integer.parseInt(br.readLine());

    long[] pado = new long[101];
    pado[0] = 0;
    pado[1] = 1;
    pado[2] = 1;
    pado[3] = 1;
    pado[4] = 2;
    pado[5] = 2;
    
    for(int j=6; j<101; j++) {
      pado[j] = pado[j-5] + pado[j-1];
    }
    
    for(int i=0; i<T; i++) {
      int N = Integer.parseInt(br.readLine());
      System.out.println(pado[N]);
    }
    
  }
}


```

<br/><br/>

## 9095 번

```java

public class b9095 {
  public static void main(String[] args) throws IOException {
    
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    int[] arr = new int[11];
    int T = Integer.parseInt(br.readLine());
    arr[1] = 1;
    arr[2] = 2;
    arr[3] = 4;
    
    for(int j=4; j<11; j++) {
      arr[j] = arr[j-1] + arr[j-2] + arr[j-3];
    }
    
    for(int i=0 ; i<T; i++) {
      int num = Integer.parseInt(br.readLine());
      System.out.println(arr[num]);
      
    }
    
  }
}

```

<br/><br/>

## 2193 번

```java

public class b2193 {
  public static void main(String[] args) throws IOException {
    
    /**
     * 이친수는 0으로 시작하지 않는다.
     * 이친수에서는 1이 두 번 연속으로 나타나지 않는다. 즉, 11을 부분 문자열로 갖지 않는다.
     */
    
     BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
     int N = Integer.parseInt(br.readLine());
     
     long[] arr = new long[91];
     
     arr[0] = 0;
     arr[1] = 1; // 1
    //  arr[2] = 1; // 10
    //  arr[3] = 2; // 100 101
    //  arr[4] = 3; // 1000 1001 1010 
    //  arr[5] = 4; // 10000 10001 10010 10101 
    //  arr[6] = 7; // 100000 100001 100010 100100 101000 101010 101001
     
     for(int i=2; i<=N; i++) {
      arr[i] = arr[i-2] + arr[i-1];
     }
    
    System.out.println(arr[N]);
     
  }
}


```

<br/><br/>

## 1463 번 🤔🤔

```java

public class b1463 {
  public static void main(String[] args) throws IOException {
    
    /**
     * https://www.acmicpc.net/problem/1463
     * 
     * 정수 X에 사용할 수 있는 연산은 다음과 같이 세 가지 이다.
     * 1. X가 3으로 나누어 떨어지면, 3으로 나눈다.
     * 2. X가 2로 나누어 떨어지면, 2로 나눈다.
     * 3. 1을 뺀다.
     * 정수 N이 주어졌을 때, 위와 같은 연산 세 개를 적절히 사용해서 1을 만들려고 한다. 
     * 연산을 사용하는 횟수의 최솟값을 출력하시오.
     */
    
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    int N = Integer.parseInt(br.readLine());
    
    int[] arr = new int[N+1];
    arr[0] = 0;
    arr[1] = 0;
    

    for(int i=2; i<=N; i++) {
      arr[i] = arr[i-1] + 1;
      if(i%2 ==0) {
        arr[i] = Math.min(arr[i], arr[i/2]+1);
      }if(i%3 ==0) {
        arr[i] = Math.min(arr[i], arr[i/3]+1);
      }
    }
    
    System.out.println(arr[N]);
    
    br.close();
  }
}


```



