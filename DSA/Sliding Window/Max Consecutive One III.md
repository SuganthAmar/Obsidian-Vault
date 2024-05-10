[Max Consecutive Ones III](https://leetcode.com/problems/max-consecutive-ones-iii/)

Given a binary array `nums` and an integer `k`, return _the maximum number of consecutive_ `1`_'s in the array if you can flip at most_ `k` `0`'s.

**Input:** nums =` [1,1,1,0,0,0,1,1,1,1,0]`, k = 2
**Output:** 6
**Explanation:** `[1,1,1,0,0,1,1,1,1,1,1]`
Bolded numbers were flipped from 0 to 1. The longest subarray is underlined.

**we are just modifying the qs to longest subarray with at most k zeros**

## Brute force
![[Pasted image 20240402214212.png]]

Generating all subarray and breaking the inner loop when the no.of zeros exceeds the k
Orelse counting the len by j-i+1

## Sliding Window

![[Pasted image 20240402214506.png]]

![[Pasted image 20240402215305.png]]

1-> When the ele is Zero increase the count of zero
2-> If the zero exceeds the k we should shrink the l to make `zero<k`
3-> if `zeros<k` find the length and updating the length

`class Solution {`
    `public int longestOnes(int[] nums, int k) {`
        `int l=0,r=0,maxlen=0,zero=0;`
        `while(r<nums.length){`
            `if(nums[r]==0){`
                `zero++;`
            `}`
            `while(zero>k){`
                `//Only when the nums[l] == 0 zero-- but every time the l increases to find the zero`
                `if(nums[l]==0){`
                    `zero--;`
                `}`
                `l++;`
            `}`
            `if(zero<=k){`
                `maxlen=Math.max(maxlen,r-l+1);`
            `}`
            `r++;`
        `}`
        `return maxlen;`
    `}`
`}`

TC = O(n)+O(n) //outer loop + inner loop
SC = O(1)

## Slight Optimization on the code to reduce the extra O(n)
![[Pasted image 20240403091159.png]]

We are just moving the l and counting the len only when k<= zero 
When the zero> k we just increasing the l pointer until the zeros within the allowed range

`class Solution {`
    `public int longestOnes(int[] nums, int k) {`
        `int l=0,r=0,maxlen=0,zero=0;`
        `while(r<nums.length){`
            `if(nums[r]==0){`
                `zero++;`
            `}`
   `//Using some optimization to Only when the nums[l] == 0 zero-- but every time the l increases to find the zero`
            `if(zero>k){`
                `if(nums[l]==0){`
                    `zero--;`
                `}`
                `l++;`
            `}`
            `if(zero<=k){`
                `maxlen=Math.max(maxlen,r-l+1);`
            `}`
            `r++;`
        `}`
        `return maxlen;`
    `}`
`}`

TC:O(n)
SC:O(1)