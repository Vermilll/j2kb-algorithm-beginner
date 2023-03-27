*2961. 도영이가 만든 맛있는 음식*
```java
import java.util.*;
import java.io.*;

public class Main{
    static int[][] arr;
    static int ans = Integer.MAX_VALUE;
    static boolean[] check;
    static int all;
    
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        all = Integer.parseInt(br.readLine());
        arr = new int[all][2];
        check = new boolean[all];
        
        for(int i=0;i<all;i++){
            StringTokenizer st = new StringTokenizer(br.readLine());
            arr[i][0] = Integer.parseInt(st.nextToken());
            arr[i][1] = Integer.parseInt(st.nextToken());
        }
        a(0);
        System.out.println(ans);
    }
    
    public static void a(int num){
        if(num == all){
            int s = 1;
            int b = 0;
            int count = 0;
            for(int i=0;i<all;i++){
                if(check[i]){
                    count++;
                    s *= arr[i][0];
                    b += arr[i][1];
                }
            }
            if(count == 0) return;
            ans = Math.min(ans, Math.abs(s - b));
	    	return;      
        }
        
        check[num] = true;
        a(num+1);
        check[num] = false;
        a(num+1);
    }
}
```

*1713. 후보 추천하기*
```java
import java.util.*;
import java.io.*;

public class Main{
    static class Vote{
        int num, count, time;
        
        Vote(int num, int count,int time){
            this.num = num;
            this.count = count;
            this.time = time;
        }
    }
    
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        int all = Integer.parseInt(br.readLine());
        int count = Integer.parseInt(br.readLine());
        LinkedList<Vote> list = new LinkedList<>();
        StringTokenizer st = new StringTokenizer(br.readLine());
        
        for(int i=0;i<count;i++){
            int vote = Integer.parseInt(st.nextToken());
            
            if(list.size() < all){
                boolean in = false;
                for(int j=0;j<list.size();j++){
                    if(list.get(j).num == vote){
                        Vote v = list.get(j);
                        list.remove(j);
                        list.add(new Vote(v.num, v.count+1, v.time));
                        in = true;
                        break;
                    }
                }
                if(!in){
                    list.add(new Vote(vote, 1, i));
                }
            }else{
                boolean in = false;
                for(int j=0;j<list.size();j++){
                    if(list.get(j).num == vote){
                        Vote v = list.get(j);
                        list.remove(j);
                        list.add(new Vote(v.num, v.count+1, v.time));
                        in = true;
                        break;
                    }
                }
                
                if(!in){
                    int minVote = Integer.MAX_VALUE;
                    int minVoteIdx = 0;
                    Stack<Vote> stack = new Stack<>();
                    
                    for(int j=0;j<list.size();j++){
                        int voteCount = list.get(j).count;
						if(minVote > voteCount) {
							minVote = voteCount;
							minVoteIdx = j;
						}
                    }
                    
                    for(int j=0;j<list.size();j++) {
						if(list.get(j).count == minVote) {
							Vote v = list.get(j);
							stack.add(v);
						}
					}
                    
                    int minTime = Integer.MAX_VALUE;
                    int minTimeNum = 0;
                    if(stack.size() == 1) {
						list.remove(minVoteIdx);
						list.add(new Vote(vote, 1, i));
					} else {
						int minTimeNumIdx = -1;
						while(!stack.isEmpty()) {
							
							Vote v = stack.pop();
							int popTime = v.time;
							if(popTime < minTime) {
								minTime = popTime;
								minTimeNum = v.num;
							}
							
							minTimeNumIdx = 0;
							for(int j=0;j<list.size();j++) {
								if(list.get(j).num == minTimeNum) {
									minTimeNumIdx = j;
								}
							}
							
						}
						list.remove(minTimeNumIdx);
						list.add(new Vote(vote, 1, i));
					}
                }
            }
        }
        StringBuilder sb = new StringBuilder();
		int[] arr = new int[list.size()];
		for(int i=0; i<list.size(); i++) {
			arr[i] = list.get(i).num;
		}
		
		Arrays.sort(arr);
		
		for(int i=0; i<arr.length; i++) {
			sb.append(arr[i]).append(" ");
		}
		
		System.out.println(sb);
    }
}
```

*15683. 감시*
```java
import java.util.*;
import java.io.*;

public class Main{
    static int ah,aw;
    static int ans;
    
    public static void main(String[] args)throws Exception{
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        StringTokenizer st1 = new StringTokenizer(br.readLine());
        ah = Integer.parseInt(st1.nextToken());
        aw = Integer.parseInt(st1.nextToken());
        int[][] arr = new int[aw][ah];
        
        for(int i=0;i<ah;i++){
            StringTokenizer st2 = new StringTokenizer(br.readLine());
            for(int j=0;j<aw;j++){
                arr[j][i] = Integer.parseInt(st2.nextToken());
            }
        }
        ans = Integer.MAX_VALUE;
        calc(arr, 0, 0);
        System.out.println(ans);
    }
    
    public static void calc(int[][] cctv, int a, int b){
        int[][] tmp;
        if(cctv[a][b] == 1){
            tmp = cloning(cctv);
            tmp = left(tmp, a, b);
            if(a != aw-1){
                calc(tmp, a+1, b);
            }else if(b != ah-1){
                calc(tmp, 0, b+1);
            }else{
                check(tmp);
            }
            
            tmp = cloning(cctv);
            tmp = up(tmp, a, b);
            if(a != aw-1){
                calc(tmp, a+1, b);
            }else if(b != ah-1){
                calc(tmp, 0, b+1);
            }else{
                check(tmp);
            }
            
            tmp = cloning(cctv);
            tmp = right(tmp, a, b);
            if(a != aw-1){
                calc(tmp, a+1, b);
            }else if(b != ah-1){
                calc(tmp, 0, b+1);
            }else{
                check(tmp);
            }
            
            tmp = cloning(cctv);
            tmp = down(tmp, a, b);
            if(a != aw-1){
                calc(tmp, a+1, b);
            }else if(b != ah-1){
                calc(tmp, 0, b+1);
            }else{
                check(tmp);
            }
        }else if(cctv[a][b] == 2){
            tmp = cloning(cctv);
            tmp = left(tmp, a, b);
            tmp = right(tmp, a, b);
            if(a != aw-1){
                calc(tmp, a+1, b);
            }else if(b != ah-1){
                calc(tmp, 0, b+1);
            }else{
                check(tmp);
            }
            
            tmp = cloning(cctv);
            tmp = up(tmp, a, b);
            tmp = down(tmp, a, b);
            if(a != aw-1){
                calc(tmp, a+1, b);
            }else if(b != ah-1){
                calc(tmp, 0, b+1);
            }else{
                check(tmp);
            }
        }else if(cctv[a][b] == 3){
            tmp = cloning(cctv);
            tmp = up(tmp, a, b);
            tmp = right(tmp, a, b);
            if(a != aw-1){
                calc(tmp, a+1, b);
            }else if(b != ah-1){
                calc(tmp, 0, b+1);
            }else{
                check(tmp);
            }
            
            tmp = cloning(cctv);
            tmp = right(tmp, a, b);
            tmp = down(tmp, a, b);
            if(a != aw-1){
                calc(tmp, a+1, b);
            }else if(b != ah-1){
                calc(tmp, 0, b+1);
            }else{
                check(tmp);
            }
            
            tmp = cloning(cctv);
            tmp = down(tmp, a, b);
            tmp = left(tmp, a, b);
            if(a != aw-1){
                calc(tmp, a+1, b);
            }else if(b != ah-1){
                calc(tmp, 0, b+1);
            }else{
                check(tmp);
            }
            
            tmp = cloning(cctv);
            tmp = left(tmp, a, b);
            tmp = up(tmp, a, b);
            if(a != aw-1){
                calc(tmp, a+1, b);
            }else if(b != ah-1){
                calc(tmp, 0, b+1);
            }else{
                check(tmp);
            }
        }else if(cctv[a][b] == 4){
            tmp = cloning(cctv);
            tmp = right(tmp, a, b);
            tmp = down(tmp, a, b);
            tmp = left(tmp, a, b);
            if(a != aw-1){
                calc(tmp, a+1, b);
            }else if(b != ah-1){
                calc(tmp, 0, b+1);
            }else{
                check(tmp);
            }
            
            tmp = cloning(cctv);
            tmp = down(tmp, a, b);
            tmp = left(tmp, a, b);
            tmp = up(tmp, a, b);
            if(a != aw-1){
                calc(tmp, a+1, b);
            }else if(b != ah-1){
                calc(tmp, 0, b+1);
            }else{
                check(tmp);
            }
            
            tmp = cloning(cctv);
            tmp = left(tmp, a, b);
            tmp = up(tmp, a, b);
            tmp = right(tmp, a, b);
            if(a != aw-1){
                calc(tmp, a+1, b);
            }else if(b != ah-1){
                calc(tmp, 0, b+1);
            }else{
                check(tmp);
            }
            
            tmp = cloning(cctv);
            tmp = up(tmp, a, b);
            tmp = right(tmp, a, b);
            tmp = down(tmp, a, b);
            if(a != aw-1){
                calc(tmp, a+1, b);
            }else if(b != ah-1){
                calc(tmp, 0, b+1);
            }else{
                check(tmp);
            }
        }else if(cctv[a][b] == 5){
            tmp = cloning(cctv);
            tmp = right(tmp, a, b);
            tmp = down(tmp, a, b);
            tmp = left(tmp, a, b);
            tmp = up(tmp, a, b);
            if(a != aw-1){
                calc(tmp, a+1, b);
            }else if(b != ah-1){
                calc(tmp, 0, b+1);
            }else{
                check(tmp);
            }
        }else{
            if(a != aw-1){
                calc(cctv, a+1, b);
            }else if(b != ah-1){
                calc(cctv, 0, b+1);
            }else{
                check(cctv);
            }
        }
    }
    
    public static int[][] left(int[][] cctv, int w, int h){
        for(int i=w-1;0<=i;i--){
            if(cctv[i][h] == 6){
                break;
            }else if(cctv[i][h] != 0){
                continue;
            }else if(cctv[i][h] == 0){
                cctv[i][h] = -1;
            }
        }
        return cctv;
    }
    
    public static int[][] right(int[][] cctv, int w, int h){
        for(int i=w+1;i<aw;i++){
            if(cctv[i][h] == 6){
                break;
            }else if(cctv[i][h] != 0){
                continue;
            }else if(cctv[i][h] == 0){
                cctv[i][h] = -1;
            }
        }
        return cctv;
    }
    
    public static int[][] up(int[][] cctv, int w, int h){
        for(int i=h-1;0<=i;i--){
            if(cctv[w][i] == 6){
                break;
            }else if(cctv[w][i] != 0){
                continue;
            }else if(cctv[w][i] == 0){
                cctv[w][i] = -1;
            }
        }
        return cctv;
    }
    
    public static int[][] down(int[][] cctv, int w, int h){
        for(int i=h+1;i<ah;i++){
            if(cctv[w][i] == 6){
                break;
            }else if(cctv[w][i] != 0){
                continue;
            }else if(cctv[w][i] == 0){
                cctv[w][i] = -1;
            }
        }
        return cctv;
    }
    
   public static void check(int[][] cctv){
       int count = 0;
       for(int i=0;i<ah;i++){
           for(int j=0;j<aw;j++){
               if(cctv[j][i] == 0){
                   count++;
               }
           }
       }
       ans = Math.min(ans, count);
   }
    
   public static int[][] cloning(int[][] a){
        int b[][] = new int[a.length][a[0].length];
	    
        for(int i=0; i<b.length; i++){
            System.arraycopy(a[i], 0, b[i], 0, a[0].length);
        }
       return b;
   }
}
```
