8393. 합  
```java
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
```
1929. 소수 구하기  
에라토스테네스의 체  
```java
import java.util.Scanner;

public class Main{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        
        int num = sc.nextInt();
        
        if(num%2!=0){return;}
        
        boolean[] arr = new boolean[num+1];
        arr[0] = true;
        arr[1] = true;
        
        for(int i=2;i*i<=num;i++){
            for(int j=i*i;j<=num;j+=i){
                arr[j] = true;
            }
        }
        
        int a = num/2;
        int b = num/2;
        
        while(true){
            while(arr[a]){a--;}
            while(arr[b]){b++;}
            
            if(a+b==num){break;}
            else if(a+b<num){b++;}
            else if(a+b>num){a--;}
        }
        
        System.out.println(a+" "+b);
    }
}
```
