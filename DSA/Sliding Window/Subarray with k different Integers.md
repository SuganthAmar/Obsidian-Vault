[992. Subarrays with K Different Integers](https://leetcode.com/problems/subarrays-with-k-different-integers/)

Given an integer array `nums` and an integer `k`, return _the number of **good subarrays** of_ `nums`.
A **good array** is an array where the number of different integers in that array is exactly `k`.

- For example, `[1,2,3,1,2]` has `3` different integers: `1`, `2`, and `3`.

A **subarray** is a **contiguous** part of an array.

**Example 1:**

**Input:** nums = `[1,2,1,2,3]`, k = 2
**Output:** 7
**Explanation:** Subarrays formed with exactly 2 different integers: `[1,2], [2,1], [1,2], [2,3], [1,2,1], [2,1,2], [1,2,1,2]`

**Modifying the qs to no.of subarray where different Integers <=k**
## Brute force
![[Pasted image 20240403134412.png]]

![[Pasted image 20240403135043.png]]

when the range of the `[l,r]` is a valid one we can form no.of valid subarrays within the range
like 3,3 1,3 1 1,....

## Method
![[Pasted image 20240403144813.png]]

![[Pasted image 20240403144855.png]]

![[Pasted image 20240403173739.png]]

```java
class Solution {
    public int subarraysWithKDistinct(int[] nums, int k) {
        return fun(nums,k)-fun(nums,k-1);
    }
    public int fun(int[] nums,int k){
        int l=0,r=0,maxlen=0;
        Map<Integer,Integer> map=new HashMap<>();
        while(r<nums.length){
            map.put(nums[r],map.getOrDefault(nums[r],0)+1);
            while(map.size()>k){
                map.put(nums[l],map.get(nums[l])-1);
                if(map.get(nums[l])==0){
                    map.remove(nums[l]);
                }
                l++;
            }
            maxlen+=r-l+1;
            r++;
        }
        return maxlen;
    }
}
```

Simple Example
```java
return fun(nums,k)-fun(nums,k-1);
```

- `fun(nums, k)` returns the count of subarrays with at most `k` distinct elements.
- `fun(nums, k-1)` returns the count of subarrays with at most `k-1` distinct elements.

So, subtracting the count of subarrays with at most `k-1` distinct elements from the count of subarrays with at most `k` distinct elements gives us the count of subarrays with exactly `k` distinct elements.

This is based on the principle that the difference between the count of subarrays with at most `k` distinct elements and the count of subarrays with at most `k-1` distinct elements gives us the count of subarrays with exactly `k` distinct elements.

Logic Expanding the window until the map size within the range if it is out of the range shrinking
when the range of the `[l,r]` is a valid one we can form no.of valid subarrays within the range
like 3,3 1,3 1 1,....
so by this we are adding the all subarray count

TC = O(2n)
SC = O(k)
