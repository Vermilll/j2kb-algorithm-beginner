*10870. 피보나치 수 5*
```java
import java.util.*;
import java.io.*;

public class Main{
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int count = Integer.parseInt(br.readLine());
        
        System.out.println(func(count));
    }
    
    public static int func(int a){
        if(a <= 1){
            return a;
        }else{
            return func(a-2) + func(a-1);
        }
    }
}
```

*17479. 재귀함수가 뭔가요?*
```java
import java.util.*;
import java.io.*;

public class Main{
    static StringBuilder sb = new StringBuilder();
    static int count;
    public static void main(String[] args){
        Scanner sc = new Scanner(System.in);
        count = sc.nextInt();
        sb.append("어느 한 컴퓨터공학과 학생이 유명한 교수님을 찾아가 물었다.").append("\n");
        func(0);
        System.out.println(sb);
    }
    
    public static void func(int a){
        String s = "";
        for(int i=0;i<a;i++){
            s += "____" ;
        }
        
        sb.append(s).append("\"재귀함수가 뭔가요?\"").append("\n");
        if(a<count){
            sb.append(s).append("\"잘 들어보게. 옛날옛날 한 산 꼭대기에 이세상 모든 지식을 통달한 선인이 있었어.").append("\n");
            sb.append(s).append("마을 사람들은 모두 그 선인에게 수많은 질문을 했고, 모두 지혜롭게 대답해 주었지.").append("\n");
            sb.append(s).append("그의 답은 대부분 옳았다고 하네. 그런데 어느 날, 그 선인에게 한 선비가 찾아와서 물었어.\"").append("\n");
            func(++a);
        }else{
            sb.append(s).append("\"재귀함수는 자기 자신을 호출하는 함수라네\"").append("\n");
        }
        sb.append(s).append("라고 답변하였지.").append("\n");
    }
}
```

*1914. 하노이 탑*
```java
```

*11729. 하노이 탑 이동 순서*
```java
```

*2630. 색종이 만들기*
```java
import java.util.*;
import java.io.*;

public class Main{
    static int white;
    static int blue;
    static int[][] paper;
    static int count;
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        count = Integer.parseInt(br.readLine());
        paper = new int[count][count];
            
        for(int i=0;i<count;i++){
            StringTokenizer st = new StringTokenizer(br.readLine());
            for(int j=0;j<count;j++){
                paper[i][j] = Integer.parseInt(st.nextToken());
            }
        }
        
        func(0,0,count);
        System.out.println(white);
        System.out.println(blue);
    }
    public static void func(int a,int b,int c){
        int color = paper[a][b];
        boolean t = true;
        
        loop:
        for(int i=a;i<a+c;i++){
            for(int j=b;j<b+c;j++){
                if(paper[i][j] != color){
                    t = false;
                    func(a,b,c/2);
                    func(a+c/2,b,c/2);
                    func(a,b+c/2,c/2);
                    func(a+c/2,b+c/2,c/2);
                    break loop;
                }
            }
        }
        
        if(t == true){
            if(paper[a][b] == 0){
                white++;
            }else{
                blue++;
            }
        }
    }
}
```

*2447. 별 찍기 - 10*
```java
import java.util.*;
import java.io.*;

public class Main{
    static int[][] star;
    public static void main(String[] args)throws Exception{
        Scanner sc = new Scanner(System.in);
        StringBuilder sb = new StringBuilder();
        int count = sc.nextInt();
        star = new int[count][count];
        
        func(0,0,count);
        
        for(int i=0;i<count;i++){
            for(int j=0;j<count;j++){
                if(star[i][j] == 1){
                    sb.append("*");
                }else{
                    sb.append(" ");
                }
            }
            sb.append("\n");
        }
        
        System.out.println(sb);
    }
    
    public static void func(int a,int b,int c){
        if(c==1){
            star[a][b] = 1;
        }else{
            func(a,b,c/3);
            func(a+c/3,b,c/3);
            func(a+c/3*2,b,c/3);
            func(a,b+c/3,c/3);
            func(a+c/3*2,b+c/3,c/3);
            func(a,b+c/3*2,c/3);
            func(a+c/3,b+c/3*2,c/3);
            func(a+c/3*2,b+c/3*2,c/3);
        }
    }
}
```

*2750. 수 정렬하기*
```java
import java.util.*;
import java.io.*;

public class Main{
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringBuilder sb = new StringBuilder();
        int count = Integer.parseInt(br.readLine());
        int[] arr = new int[count];
        for(int i=0;i<count;i++){
            arr[i] = Integer.parseInt(br.readLine());
        }
        Arrays.sort(arr);
        for(int a : arr){
            sb.append(a).append("\n");
        }
        System.out.println(sb);
    }
}
```

*10989. 수 정렬하기3*
```java
import java.util.*;
import java.io.*;

public class Main{
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringBuilder sb = new StringBuilder();
        int count = Integer.parseInt(br.readLine());
        int[] arr = new int[count];
        for(int i=0;i<count;i++){
            arr[i] = Integer.parseInt(br.readLine());
        }
        Arrays.sort(arr);
        for(int a : arr){
            sb.append(a).append("\n");
        }
        System.out.println(sb);
    }
}
```

*10814. 나이순 정렬*
```java
import java.util.*;
import java.io.*;

public class Main{
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringBuilder sb = new StringBuilder();
        int count = Integer.parseInt(br.readLine());
        String[] s = new String[count];
        
        for(int i=0;i<count;i++){
            s[i] = br.readLine();
        }
        
        Arrays.sort(s, new Comparator<String>() {
			@Override
			public int compare(String s1, String s2) {
				return Integer.parseInt(s1.split(" ")[0]) - Integer.parseInt(s2.split(" ")[0]);
			}
		});
        
        for(int i=0;i<count;i++){
            sb.append(s[i]).append("\n");
        }
        
        System.out.println(sb);
    }
}
```

*1427. 소트인사이드*
```java
import java.util.*;
import java.io.*;

public class Main{
    public static void main(String[] args)throws Exception{
        Scanner sc = new Scanner(System.in);
        StringBuilder sb = new StringBuilder();
        String s = sc.nextLine();
        String[] n = new String[s.length()];
        
        n = s.split("");
        Arrays.sort(n);
        
        for(int i=s.length()-1;i>=0;i--){
            sb.append(n[i]);
        }
        System.out.println(sb);
    }
}
```

*2947. 나무조각*
```java
import java.util.*;
import java.io.*;

public class Main{
    public static void main(String[] args)throws Exception{
        StringBuilder sb = new StringBuilder();
        Scanner sc = new Scanner(System.in);
        String a = sc.nextLine();
        String[] s = a.split(" ");
        while(true){
            boolean change = false;
            for(int j=0;j<4;j++){
                if(Integer.parseInt(s[j])>Integer.parseInt(s[j+1])){
                    change = true;
                    String temp = s[j+1];
                    s[j+1] = s[j];
                    s[j] = temp;
                    
                    for(int k=0;k<5;k++){
                        sb.append(s[k] + " ");
                    }
                    sb.append("\n");
                }
            }
            if(!change){break;}
        }
        System.out.println(sb);
    }
}
```

*1431. 시리얼 번호*
```java
import java.util.*;
import java.io.*;

public class Main{
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringBuilder sb = new StringBuilder();
        int count = Integer.parseInt(br.readLine());
        String[] arr = new String[count];
        for(int i=0;i<count;i++){
            arr[i] = br.readLine();
        }
        
        for(int i=0;i<count;i++){
            for(int j=0;j<count-1;j++){
                if(arr[j].length() == arr[j+1].length()){
                    int num1 = 0;
                    int num2 = 0;
                    String[] s1 = arr[j].split("");
                    String[] s2 = arr[j+1].split("");
                    
                    for(String a : s1){
                        if(a.charAt(0) >= '1' && a.charAt(0) <= '9'){
                            num1 += Integer.parseInt(a);
                        }
                    }
                    for(String a : s2){
                        if(a.charAt(0) >= '1' && a.charAt(0) <= '9'){
                            num2 += Integer.parseInt(a);
                        }
                    }
                    
                    if(num1 > num2){
                        String temp = arr[j];
                        arr[j] = arr[j+1];
                        arr[j+1] = temp;
                    }else if(num1 == num2){
                        for(int k=0;k<arr[j].length();k++){
                            if(arr[j].charAt(k) < arr[j+1].charAt(k)){
                                break;
                            }else if(arr[j].charAt(k) > arr[j+1].charAt(k)){
                                String temp = arr[j];
                                arr[j] = arr[j+1];
                                arr[j+1] = temp;
                                break;
                            }
                        }
                    }
                }else if(arr[j].length() > arr[j+1].length()){
                    String temp = arr[j];
                    arr[j] = arr[j+1];
                    arr[j+1] = temp;
                }
            }
        }
        
        for(int i=0;i<count;i++){
            sb.append(arr[i]).append("\n");
        }
        System.out.println(sb);
    }
}
```

*18870. 좌표 압축*
```java
import java.util.*;
import java.io.*;

public class Main{
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int count = Integer.parseInt(br.readLine());
        StringTokenizer st = new StringTokenizer(br.readLine());
        StringBuilder sb = new StringBuilder();
        int[] arr = new int[count];
        int[] ref = new int[count];
        HashMap<Integer, Integer> map = new HashMap<Integer, Integer>();
        for(int i=0;i<count;i++){
            arr[i] = ref[i] = Integer.parseInt(st.nextToken());
        }
        Arrays.sort(ref);
        
        int rank = 0;
        for(int i=0;i<count;i++){
            int a = ref[i];
            if(!map.containsKey(a)) {
				map.put(a, rank);
				rank++;
			}
        }
        
        for(int i=0;i<count;i++){
            sb.append(map.get(arr[i]) + " ");
        }
        System.out.println(sb);
    }
}
```
