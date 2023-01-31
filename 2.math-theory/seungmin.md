8393. 합  
```
import java.util.Scanner;

public class Main{
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);
 
		int num = sc.nextInt();
		int sum = 0;
        
		for (int i = 1; i <= num; i++) {
			sum += i;
		}
		System.out.println(sum);
	}
}
```java
1929. 소수 구하기  
에라토스테네스의 체  
https://namu.wiki/w/%EC%97%90%EB%9D%BC%ED%86%A0%EC%8A%A4%ED%85%8C%EB%84%A4%EC%8A%A4%EC%9D%98%20%EC%B2%B4
```
import java.util.Scanner;

public class Main{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        
        int min = sc.nextInt();
        int max = sc.nextInt();
        
        boolean arr[] = new boolean[max+1];
        arr[0] = true;
        arr[1] = true;
        
        for(int i=2;i*i<=max+1;i++){
            for(int j=i*i;j<max+1;j+=i){
                arr[j] = true;
            }
        }
        
        for(int i=min;i<max+1;i++){
            if(arr[i] == false){
                System.out.println(i);   
            }
        }
    }
}
```
1978. 소수 찾기  
```java
import java.util.Scanner;

public class Main{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        int all = sc.nextInt();
        int count = all;
        
        for(int i=0;i<all;i++){
            int num = sc.nextInt();
            
            if(num==0 || num==1){
                count--;
                continue;
            }else if(num==2){
                continue;
            }
            
            for(int j=2;j<num;j++){
                if(num%j==0){
                    count--;
                    break;
                }
            }
        }
        
        System.out.println(count);
    }
}
```
4948. 베르트랑 공준  
```java
import java.util.Scanner;

public class Main{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        boolean arr[] = new boolean[2*123456+1];
        
        arr[0] = true;
        arr[1] = true;
        
        while(true){
            int count = 0;
            int num = sc.nextInt();
            
            if(num == 0){break;}
            
            for(int i=2;i*i<=2*num;i++){
                for(int j=i*i;j<=2*num;j+=i){
                    arr[j] = true;
                }
            }
            
            for(int i=num+1;i<=2*num;i++){
                if(arr[i]==false){
                    count++;
                }
            }
            
            System.out.println(count);
        }
    }
}
```
15649. N과 M(1)  
백 트래킹
```java
import java.util.Scanner;
 
public class Main {
	static int[] arr;
	static boolean[] use;
	static int N, M;
    
	public static void main(String[] args) {
 
		Scanner sc = new Scanner(System.in);
 
        N = sc.nextInt();
        M = sc.nextInt();
 
		use = new boolean[N];
		arr = new int[M];
		dfs(0);
	}
 
	public static void dfs(int depth) {
		if (depth == M) {
			for (int val : arr) {
				System.out.print(val + " ");
			}
			System.out.println();
			return;
		}
 
		for (int i = 0; i < N; i++) {
			if (!use[i]) {
				use[i] = true;
				arr[depth] = i + 1;
				dfs(depth + 1);
				use[i] = false;
			}
		}
	}
}
```
