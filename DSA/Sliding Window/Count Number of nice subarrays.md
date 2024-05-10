[1248. Count Number of Nice Subarrays](https://leetcode.com/problems/count-number-of-nice-subarrays/)

Given an array of integers `nums` and an integer `k`. A continuous subarray is called **nice** if there are `k` odd numbers on it.

Return _the number of **nice** sub-arrays_.

**Example 1:**

**Input:** nums = [1,1,2,1,1], k = 3
**Output:** 2
**Explanation:** The only sub-arrays with 3 odd numbers are [1,1,2,1] and [1,2,1,1].

## Same problem like binary Substring with sum

```java
class Solution {
    public int numberOfSubarrays(int[] nums, int k) {
        return f(nums,k) - f(nums,k-1);
    }
    public int f(int[] nums,int k){
        int l=0,r=0,odd=0,count=0;
        while(r<nums.length){
            if(nums[r]%2==1) odd++;
            while(odd>k){
                if(nums[l]%2==1){
                    odd--;
                }
                l++;
            }
            count+=(r-l+1);
            r++;
        }
        return count;
    }
}
```