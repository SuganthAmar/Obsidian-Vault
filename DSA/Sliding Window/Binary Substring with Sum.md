[930. Binary Subarrays With Sum](https://leetcode.com/problems/binary-subarrays-with-sum/)

Given a binary array `nums` and an integer `goal`, return _the number of non-empty **subarrays** with a sum_ `goal`.

A **subarray** is a contiguous part of the array.

**Example 1:**

**Input:** nums = [1,0,1,0,1], goal = 2
**Output:** 4
**Explanation:** The 4 subarrays are bolded and underlined below:
[1,0,1,0,1]
[1,0,1,0,1]
[1,0,1,0,1]
[1,0,1,0,1]

### Just modify the question to :
**no of subarrays where sum <= goal**

![[Pasted image 20240409173919.png]]


Simple Math to get exactly that goal

![[Pasted image 20240409174129.png]]

```java
class Solution {
    public int numSubarraysWithSum(int[] nums, int goal) {
        return find(nums,goal)-find(nums,goal-1);  
    }
    public int find(int[] nums,int k){
        if(k<0) return 0;
        int n=nums.length;
        int start=0,end=0;
        int cnt=0;
        int curr=0;
        while(end<nums.length){
            curr+=nums[end];
            while(curr>k) curr-=nums[start++];
            cnt+=(end-start+1);
            end++;
        }
        return cnt;
    }
}
```
