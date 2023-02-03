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
 
		for (int i=0;i<N;i++) {
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

2609. 최대공약수와 최소공배수  
유클리드 호제법  
```java
import java.util.Scanner;

public class Main{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        
        int a = sc.nextInt();
        int b = sc.nextInt();
        
        int c = a;
        int d = b;
        while(d!=0){
            int temp = c%d;
            c = d;
            d = temp;
        }
        System.out.println(c);
        System.out.println(a*b/c);
    }
}
```

9020. 골드바흐의 추측  
에라토스테네스의 체  
```java
import java.util.Scanner;

public class Main{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        
        int count = sc.nextInt();
        
        boolean[] arr = new boolean[10001];
        arr[0] = true;
        arr[1] = true;
        
        for(int c=0;c<count;c++){
            int num = sc.nextInt();
            
            for(int i=2;i*i<=num;i++){
                if(arr[i]){continue;}
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
}
```

11653. 소인수분해  
```java
import java.util.*;

public class Main{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        
        int num = sc.nextInt();
        int a = 2;
        while(num>1){
            if(num%a==0){
                num /= a;
                System.out.println(a);
            }else{a++;}
        }
    }
}
```

6588. 골드바흐의 추측
```java
import java.util.*;

public class Main{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        int num = sc.nextInt();
        boolean[] arr = new boolean[1000001];
        arr[0] = true;
        arr[1] = true;
            
            for(int i=2;i*i<=1000000;i++){
                if(arr[i]){continue;}
                for(int j=i*i;j<=1000000;j+=i){
                    arr[j] = true;
                }
            }
        
        while(num!=0){
            
            int a = 3;
            int b = num-1;
            
            while(true){
                while(arr[a] && a<b){a+=2;}
                while(arr[b] && a<b){b-=2;}
                
                if(a>b){
                    System.out.println("Goldbach's conjecture is wrong.");
                    break;
                }
                
                if(a+b==num){
                    System.out.println(num+" = "+a+" + "+b);
                    break;
                }
                else if(a+b<num){a+=2;}
                else if(a+b>num){b-=2;}
                
            }
            
            num = sc.nextInt();
        }
    }
}
```

1182. 부분수열의 합
```java
import java.util.*;

public class Main{
    static int depth, num, count;
    static int[] arr;
    
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        depth = sc.nextInt();
        num = sc.nextInt();
        arr = new int[depth];
        count = 0;
        
        for(int i=0;i<depth;i++){
            arr[i] = sc.nextInt();
        }
        
        dfs(0,0);
        if(num == 0){count--;}
        
        System.out.println(count);
    }
    
    public static void dfs(int dep,int sum){
        if(dep == depth){
            if(sum == num){count++;}
            return;
        }
        
        dfs(dep+1,sum + arr[dep]);
        dfs(dep+1,sum);
    }
}
```

6603. 로또
```java
import java.util.*;

public class Main{
    static int count;
    static int[] num;
    static int[] temp;
        
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        
        while(true){
            count = sc.nextInt();
            if(count == 0){break;}
            
            num = new int[count];
            temp = new int[6];
            
            for(int i=0;i<count;i++){
                num[i] = sc.nextInt();
            }
            
            dfs(0,0,temp);
            System.out.println();
        }
    }
    
    public static void dfs(int depth,int cursor,int[] temp){
        if(cursor>count){return;}
        
        if(depth == 6){
            for(int i=0;i<6;i++){System.out.print(temp[i]+" ");}
            System.out.println();
            return;
        }
        
        for(int i=1;i<count-cursor+1;i++){
            temp[depth] = num[cursor+i-1];
            dfs(depth+1,cursor+i,temp);
        }
    }
}
```

15650. N과 M (2)
```java
import java.util.*;

public class Main{
    static int N, M;
    static int[] temp;
    
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        N = sc.nextInt();
        M = sc.nextInt();
        temp = new int[M];
        
        dfs(0,0,temp);
    }
    
    public static void dfs(int depth,int cursor,int[] temp){
        if(cursor>N){
            return;
        }
        
        if(depth == M){
            for(int i=0;i<M;i++){
                System.out.print(temp[i]+" ");
            }
            System.out.println();
            return;
        }
        
        for(int i=1;i<N-cursor+1;i++){
            temp[depth] = cursor+i;
            dfs(depth+1,cursor+i,temp);
        }
    }
}
```

2981. 검문
```java
import java.util.*;

public class Main {
	public static int GCD(int a, int b) {
		
		if(b == 0) return a;
		else return GCD(b, a%b);
	}
	
	public static void main(String[] args) {
		Scanner sc = new Scanner(System.in);

		int count = sc.nextInt();
		int arr[] = new int[count];
		for (int i=0;i<count;i++) {
			arr[i] = sc.nextInt();
		}
		Arrays.sort(arr);
		
		int dif = arr[1] - arr[0];
		for (int i=2;i<count;i++) {
			dif = GCD(dif, arr[i] - arr[i-1]);
		}
		
		for (int i=2;i<dif;i++) {
			if(dif%i==0) {System.out.print(i+" ");}
		}
		System.out.print(dif+" ");
	}
}
```

2407. 조합
```java
import java.util.*;
import java.math.*;

public class Main{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        int m = sc.nextInt();
        if(m<n/2){
            m = n-m;
        }
        
        BigInteger ans = new BigInteger("1");
        for(int i=m+1;i<=n;i++){
            ans = ans.multiply(new BigInteger(String.valueOf(i))); 
        }
        
        for(int i=1;i<=n-m;i++){
            ans = ans.divide(new BigInteger(String.valueOf(i)));
        }
        
        System.out.println(ans);
    }
}
```

10974. 모든 순열
```java
import java.util.*;

public class Main{
    static int count;
    static int[] arr;
    static boolean[] check;
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        count = sc.nextInt();
        arr = new int[count];
        check = new boolean[count];
        
        dfs(0);
    }
    
    public static void dfs(int depth){
        if(depth == count){
            for(int i=0;i<count;i++){
                System.out.print(arr[i] + " ");
            }
            System.out.println();
            return;
        }
        
        for (int i=0;i<count;i++) {
			if (!check[i]) {
				check[i] = true;
				arr[depth] = i+1;
				dfs(depth+1);
				check[i] = false;
			}
		}
    }
}
```
2824. 최대공약
```java
import java.util.*;
import java.math.*;

public class Main{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        
        int count = sc.nextInt();
        BigInteger a = new BigInteger("1");
        for(int j=0;j<count;j++){
            a = a.multiply(new BigInteger(String.valueOf(sc.nextInt())));
        }
        
        count = sc.nextInt();
        BigInteger b = new BigInteger("1");
        for(int j=0;j<count;j++){
            b = b.multiply(new BigInteger(String.valueOf(sc.nextInt())));
        }
        
        String c;
        
        if(a.compareTo(b)>0){
            c = gcd(b,a).toString();
        }else{
            c = gcd(a,b).toString();
        }
        
        if(c.length()>9){
            c = c.substring(c.length()-9);
        }
        
        System.out.println(c);
    }
    
    public static BigInteger gcd(BigInteger a,BigInteger b){
        if(b.compareTo(new BigInteger("0"))==0){
            return a;
        }else{
            return gcd(b,a.remainder(b));
        }
    }
}
```
17103. 골드바흐 파티션
```java
import java.util.*;

public class Main{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        int count;
        int k = sc.nextInt();
        boolean[] arr = new boolean[1000001];
        arr[0] = true;
        arr[1] = true;
        
        for(int i=2;i*i<=1000000;i++){
                if(arr[i]){continue;}
                for(int j=i*i;j<=1000000;j+=i){
                    arr[j] = true;
                }
        }
        
        for(int i=0;i<k;i++){
            int num = sc.nextInt();
            count = 0;
            if(num%2!=0){continue;}
            
            int a = 2;
            int b = num-1;
            while(a<=b){
                while(arr[a]){a++;}
                while(arr[b]){b--;}
                if(a>b){break;}
                
                if(a+b == num){
                    b--;
                    a++;
                    count++;
                }
                else if(a+b > num){b--;}
                else if(a+b < num){a++;}
            }
            
            System.out.println(count);
        }
    }
}
```
17087. 숨바꼭질6
```java
import java.util.*;

public class Main{
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        
        int count = sc.nextInt();
        int num = sc.nextInt();
        
        int[] arr = new int[count];
        for(int i=0;i<count;i++){
            arr[i] = num - sc.nextInt();
            if(arr[i]<0){arr[i] = -arr[i];}
        }
        
        Arrays.sort(arr);
        int ans = arr[0];
        
        for(int i=1;i<=count;i++){
            ans = def(ans, arr[i-1]);
        }
        
        System.out.println(ans);
    }
    
    public static int def(int a,int b){
        if(b==0){return a;}
        else{return def(b,a%b);}
    }
}
```
