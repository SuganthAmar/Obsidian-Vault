
Given a string, find the length of the longest substring T that contains at most _k_ distinct characters.

**Example 1:**

**Input:** s = "eceba", k = 2
**Output:** 3
**Explanation:** T is "ece" which its length is 3.

![[Pasted image 20240403185006.png]]

## Brute Force
![[Pasted image 20240403185251.png]]
![[Pasted image 20240403185334.png]]


## Sliding window Apporach
```java
package Sliding_Window;
import java.util.*;
public class Longest_Substring_With_At_Most_K_Distinct_Characters {
    public static void main(String[] args) {
        Scanner sc=new Scanner(System.in);
        String s=sc.next();
        int k=sc.nextInt();
        int res=fun(s,k);
        System.out.println("Answer = "+res);
    }
    public static int fun(String s,int k){
        int l=0,r=0,maxlen=0;
        Map<Character,Integer> map=new HashMap<>();
        while(r<s.length()){
            char chr=s.charAt(r);
            char chl=s.charAt(l);
            map.put(chr,map.getOrDefault(chr,0)+1);
            while(map.size()>k){ // use (if)
                map.put(chl,map.get(chl)-1);
                if(map.get(chl)==0){
                    map.remove(chl);
                }
                l++;
            }
            maxlen=Math.max(maxlen,r-l+1);
            r++;
        }
        return maxlen;
    }
}
```

TC=O(n)
SC=O(k)


