# 1929 소수 구하기

```java
public class b1929 {

  public static void main(String[] args) throws IOException {
    
     BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
     BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(System.out));
     
    StringTokenizer st = new StringTokenizer(br.readLine());
    
    int startN = Integer.parseInt(st.nextToken());
    int endN = Integer.parseInt(st.nextToken());
    
    
    int[] arr = DecimalNum(endN);
    for(int i = startN; i<=endN; i++) {
      if(arr[i] != 0) {
        bw.write(String.valueOf(i) + '\n');
      }
    }
    
     bw.flush();
     bw.close();
     br.close();
     
  }
  
  // 에라토스테네스의 체 사용
  public static int[] DecimalNum(int num) {
    int arr[] = new int[num+1]; // 31-1 =30
    
    for(int i=2; i<=num; i++) { // 2~30
      arr[i] = i;
    }
    
    for(int i=2; i<=num; i++) {
      if(arr[i] == 0) continue;
      for(int j=i+i; j<=num; j+=i) {
        arr[j] = 0;
      }
    }
    
    return arr;
  }
  
  // 에라토스테네스의 체 사용 전
  public static boolean compareDecimal(int num) {
    for(int i=2; i<=num; i++) {
      if(i == num) {
        return true;
      }
      if(num % i ==0) {
        break;
      }
    }
  
    return false;  
  }
  
}

```

---

# 4948 베르트랑 공준

```java
public class b4948 {
  public static void main(String[] args) throws IOException {
    /**
     * 각 테스트 케이스에 대해서, n보다 크고, 2n보다 작거나 같은 소수의 개수를 출력한다.
     * 입력의 마지막에는 0이 주어진다.
     */
    
    BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
    int num = 0;
    
    while(true){
      num = Integer.parseInt(br.readLine());
      if(num == 0) break;
      
      int result = countDecimal(num);
      System.out.println(result);
      
    } 
    
  }
  
  public static int countDecimal(int num) {
    int end = num*2;
    int count = 0;
    int[] arr = new int[end+1];
    
    for(int i=2; i<=end; i++) {
      arr[i] = i;
    }
    
    for(int i=2; i<=end; i++) {
      if(arr[i] == 0) continue;
      for(int j=i+i; j<=end; j+=i) {
        arr[j] = 0;
      }
    }
    
    for(int i=num+1; i<=end; i++) {
      if(arr[i] != 0) {
        count++;
      }
    }
    
    return count;
  }
  
}
```



