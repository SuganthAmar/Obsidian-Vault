[424. Longest Repeating Character Replacement](https://leetcode.com/problems/longest-repeating-character-replacement/)

You are given a string `s` and an integer `k`. You can choose any character of the string and change it to any other uppercase English character. You can perform this operation at most `k` times.

Return _the length of the longest substring containing the same letter you can get after performing the above operations_.

**Example 1:**

**Input:** s = "ABAB", k = 2
**Output:** 4
**Explanation:** Replace the two 'A's with two 'B's or vice versa.

**Solution**
We are going to use the length - maxfreq formula to find the maximum repeating character so we can change other character to this character

## Brute force
![[Pasted image 20240408214500.png]]
## Typo :`hash[s[j]]++ -> hash[s[j]-'A`]++;`

-> We are using the loop one to generate all the substring 
-> We can create a hash map every time the character starts and starts counting the occurrence
of the char to find the maxfreq
-> And we are calculating the no of chance from the maxfreq
AAABB from i =0 A=3 maxFreq is A and it calculate the how many character needs to be changed 
if j=4 so it's 2
-> That changes is less then or equal to the k we can change

![[Pasted image 20240408215228.png]]

![[Pasted image 20240408221801.png]]
![[Pasted image 20240408221820.png]]


```java
class Solution {
    public int characterReplacement(String s, int k) {
        int l=0,r=0,maxfreq=0,maxlen=0;
        int change=0;
        int[] hash=new int[26];
        while(r<s.length()){
            hash[s.charAt(r)-'A']++;
            maxfreq=Math.max(hash[s.charAt(r)-'A'],maxfreq);
            change=(r-l+1)-maxfreq;
            while(change>k){
                hash[s.charAt(l)-'A']--;
                maxfreq=0;
                for(int i=0;i<26;i++){
                    maxfreq=Math.max(maxfreq, hash[i]);
                }
                change--;
                l++;
            }
            if(change<=k){
                maxlen=Math.max(r-l+1,maxlen);
            }
            r++;
        }
       return maxlen;
    }
}
```

TC = O(N+N) x 26
SC = O(26)

Slight optimisation
``` java
class Solution {
    public int characterReplacement(String s, int k) {
        int l=0,r=0,maxfreq=0,maxlen=0;
        int change=0;
        int[] hash=new int[26];
        while(r<s.length()){
            hash[s.charAt(r)-'A']++;
            maxfreq=Math.max(hash[s.charAt(r)-'A'],maxfreq);
            change=(r-l+1)-maxfreq;
            if(change>k){
                hash[s.charAt(l)-'A']--;
                maxfreq=0;
                change--;
                l++;
            }
            if(change<=k){
                maxlen=Math.max(r-l+1,maxlen);
            }
            r++;
        }
        return maxlen;
    }
}
```


TC = O(N) 
SC = O(26)


-> Updating the Character count
-> If it exceeds the k we just decreasing the character at l
-> and updating the maxfreq to 0 so at next iteration the maxfreq will update
-> calculating the maxlen