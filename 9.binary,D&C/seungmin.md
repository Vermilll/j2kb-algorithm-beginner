*2448. 별 찍기 - 11*
```java
import java.io.*;
import java.util.*;

public class Main{
    static boolean[][] star;
    public static void main(String[] args){
        StringBuilder sb = new StringBuilder();
        Scanner sc = new Scanner(System.in);
        int num = sc.nextInt();
        star = new boolean[num*2][num];
        re(0,0,num);
        
        for(int i=0;i<num;i++){
            for(int j=0;j<num*2;j++){
                if(star[j][i]){
                    sb.append("*");
                }else{
                    sb.append(" ");
                }
            }
            sb.append("\n");
        }
        
        System.out.println(sb);
    }
    
    public static void re(int a, int b, int c){
        if(c == 3){
            star[a+2][b] = true;
            star[a+1][b+1] = star[a+3][b+1] = true;
            star[a][b+2] = star[a+1][b+2] = star[a+2][b+2] = star[a+3][b+2] = star[a+4][b+2] = true;
        }else{
            re(a+c/2, b, c/2);
            re(a, b+c/2, c/2);
            re(a+c, b+c/2, c/2);
        }
    }
}
```
