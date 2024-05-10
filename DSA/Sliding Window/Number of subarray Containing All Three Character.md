[1358. Number of Substrings Containing All Three Characters](https://leetcode.com/problems/number-of-substrings-containing-all-three-characters/)

Given a string `s` consisting only of characters _a_, _b_ and _c_.

Return the number of substrings containing **at least** one occurrence of all these characters _a_, _b_ and _c_.

**Example 1:**

**Input:** s = "abcabc"
**Output:** 10
**Explanation:** The substrings containing at least one occurrence of the characters _a_, _b_ and _c are `"_abc_", "_abca_", "_abcab_", "_abcabc_", "_bca_", "_bcab_", "_bcabc_", "_cab_", "_cabc_"_ and _"_abc_".`

## Brute Force
![[Pasted image 20240405213207.png]]

Shuttle Optimisation 
![[Pasted image 20240405213437.png]]

If we got three character at the index 3 and the length is six after that all the character is valid so we can straight away add the position and the length to the answer

![[Pasted image 20240405213734.png]]\
For every character we know it's end

## Approach -2
![[Pasted image 20240406085906.png]]

-> We are updating the last seen of the three character and finding the minimum of all the three 
-> So now we know from where the window is starting and before that index also it is possible to form the substring so adding 1 as this string and adding the min of the three values

![[Pasted image 20240406090210.png]]


```java
class Solution {
    public int numberOfSubstrings(String s) {
        int[] index={-1,-1,-1};
        int count=0;
        for(int i=0;i<s.length();i++){
            char ch=s.charAt(i);
            index[ch-'a']=i;
            if(index[0]!=-1 && index[1]!=-1 && index[2]!=-1){
                int mini=Arrays.stream(index).min().getAsInt();
                count=count+mini+1;
            }
        }
        return count;
    }
}
```

TC=O(n)
SC=O(1)
