[Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)


![[Pasted image 20240402184151.png]]

Answer is `cadbz` or `zabcd` with length 5

## Brute force

![[Pasted image 20240402184657.png]]
Generating all substring and storing the previous occurrence of the character in the `hash[256]`
so when `hash[s[i]]==1` we can break because it's asking for the non repeating character 

We can also find the length and we need to store the maximum length so far to get the maximum length

## Sliding window

![[Pasted image 20240402185207.png]]

Consider a hash map
![[Pasted image 20240402185302.png]]
![[Pasted image 20240402185445.png]]
-> at this point the a is already seen in the map so moving the l pointer +1 is not correct because a is found at r'th position 
-> so we need to move the pointer next to a 
-> so `l=mpp.get('a')+1` so now a move to 2nd index at 'd'
-> after that update the map of a to 5th index


### Method -1
`class Solution {`
    `public int lengthOfLongestSubstring(String s) {`
        `Map<Character,Integer> map=new HashMap<>();`
        `int l=0,r=0;`
        `int maxlen=0;`
        `while(r<s.length()){`
            `char ch=s.charAt(r);`
            `int len=0;`
            `if(map.containsKey(ch)){`
                `if(map.get(ch)>=l){`
                    `l=map.get(ch)+1;`
                `}`
            `}`
                `map.put(ch,r);`
                `len=r-l+1;`
            `r++;`
            `maxlen=Math.max(maxlen,len);`
        `}`
        `return maxlen;`
    `}`
`}`

### Method - 2:
`class Solution {` 
`public int lengthOfLongestSubstring(String s) {` 
`int[] hash=new int[256];`
`Arrays.fill(hash,-1);`
`int l=0,r=0,maxlen=0;` 
`while(r<s.length()){` 
	`int ch=s.charAt(r);` 
	`if(hash[ch]!=-1){` 
		`if(hash[ch]>=l){` 
			`l=hash[ch]+1;`
			`}`
		`}`
	`hash[ch]=r;` 
	`maxlen=Math.max(maxlen,r-l+1);` 
	`r++;`
	 `}`
	  `return maxlen;` 
	  `}`
 `}`

Why this condition 
`if(hash[ch]>=l){` 
	`l=hash[ch]+1;`
	`}`

For this input:
s ="abba"
a->0
b->1
next r at 3rd index already found so whether the r'th position is greater the l that means that is within the l-r range
b->2
and r at 3th index a is aleardy there so updation is like l=hash[r]+1 but which is going back from l so it not valid because of that we need to consider the valid range 

**Reason**
1. When encountering a character that is already in the map, it implies that there is a repeating character.
2. `map.get(ch)` retrieves the index of the last occurrence of the character `ch`.
3. If the index of the last occurrence of the character is greater than or equal to the current value of `l`, it means that this occurrence is within the current window of characters (`[l, r]`), and updating `l` to `map.get(ch) + 1` ensures that `l` moves to the next position after the previous occurrence of the repeating character.
4. This step ensures that we maintain a valid substring without repeating characters.

### Here's why it's necessary:

- Suppose we have a string "abba" and `l = 0`, `r = 3`. When `r` points to the second 'a', `l` should be updated to `map.get('a') + 1` because we don't want to consider the first 'a' again. If we don't update `l`, it will remain at 0, and we will count 'a' again, resulting in an invalid substring.
- By updating `l` to `map.get(ch) + 1`, we ensure that the substring `[l, r]` remains valid and doesn't contain any repeating characters.

TC: O(n)
SC:O(256)
