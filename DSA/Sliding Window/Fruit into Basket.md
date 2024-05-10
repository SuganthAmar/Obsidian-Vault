[Fruit Into Baskets](https://leetcode.com/problems/fruit-into-baskets/)

You are visiting a farm that has a single row of fruit trees arranged from left to right. The trees are represented by an integer array `fruits` where `fruits[i]` is the **type** of fruit the `ith` tree produces.

You want to collect as much fruit as possible. However, the owner has some strict rules that you must follow:

- You only have **two** baskets, and each basket can only hold a **single type** of fruit. There is no limit on the amount of fruit each basket can hold.
- Starting from any tree of your choice, you must pick **exactly one fruit** from **every** tree (including the start tree) while moving to the right. The picked fruits must fit in one of your baskets.
- Once you reach a tree with fruit that cannot fit in your baskets, you must stop.

Given the integer array `fruits`, return _the **maximum** number of fruits you can pick_.

**Example 1:**

**Input:** fruits = `[1,2,1]`
**Output:** 3
**Explanation:** We can pick from all 3 trees.

## Observation :
Just convert this qs to -> **max length of the subarray with at most two type of numbers**

## Brute force 
![[Pasted image 20240403092725.png]]

We are just generating all possible subarray and then checking the unique type using a set data structure

## Sliding window approach -1 :
![[Pasted image 20240403122721.png]]
![[Pasted image 20240403122853.png]]

Adding the new element to the map and at when this map size exceeds the k we should trim the 
length until the map size is less then or equal to k

`class Solution {`
    `public int totalFruit(int[] fruits) {`
        `int l=0,r=0,maxlen=0,k=2;`
        `Map<Integer,Integer> map=new HashMap<>();`
        `while(r<fruits.length){`
            `map.put(fruits[r],map.getOrDefault(fruits[r],0)+1);`
            `if(map.size()>k){`
                `while(map.size()>k){`
                    `map.put(fruits[l],map.get(fruits[l])-1);`
                    `if(map.get(fruits[l])==0){`
                        `map.remove(fruits[l]);`
                    `}`
                    `l++;`    
                `}`
            `}`
            `if(map.size()<=k){`
                `maxlen=Math.max(maxlen,r-l+1);`
            `}`
            `r++;`
        `}`
        `return maxlen;`
    `}`
`}`

TC = O(n)+O(n)
SC = O(2)


## Slightly optimised code
`class Solution {`
    `public int totalFruit(int[] fruits) {`
        `int l=0,r=0,maxlen=0,k=2;`
        `Map<Integer,Integer> map=new HashMap<>();`
        `while(r<fruits.length){`
            `map.put(fruits[r],map.getOrDefault(fruits[r],0)+1);`
            `if(map.size()>k){`
                `map.put(fruits[l],map.get(fruits[l])-1);`
                `if(map.get(fruits[l])==0){`
                    `map.remove(fruits[l]);`
                `}`
                `l++;`    
            `}`
            `if(map.size()<=k){`
                `maxlen=Math.max(maxlen,r-l+1);`
            `}`
            `r++;`
        `}`
        `return maxlen;`
    `}`
`}`

-> Just using the single while loop so the extra tc of O(n) with inner loop is reduced
TC=O(n)
