[Maximum Points You Can Obtain from Cards](https://leetcode.com/problems/maximum-points-you-can-obtain-from-cards/)

There are several cards **arranged in a row**, and each card has an associated number of points. The points are given in the integer array `cardPoints`.

In one step, you can take one card from the beginning or from the end of the row. You have to take exactly `k` cards.

Your score is the sum of the points of the cards you have taken.

Given the integer array `cardPoints` and the integer `k`, return the _maximum score_ you can obtain.

**Example 1:**

**Input:** cardPoints = [1,2,3,4,5,6,1], k = 3
**Output:** 12
**Explanation:** After the first step, your score will always be 1. However, choosing the rightmost card first will maximize your total score. The optimal strategy is to take the three cards on the right, giving a final score of 1 + 6 + 5 = 12.

![[Pasted image 20240329133219.png]]

1-> Add the element sum upto the window size
2-> reduce one from left side add one to the right side

![[Pasted image 20240329133455.png]]

TC-> O(2k)
SC-> O(1)

## Code
`class Solution {`
    `public int maxScore(int[] cardPoints, int k) {`
        `int leftsum=0;`
        `int rightsum=0;`
        `int maxi=0;`
        `for(int i=0;i<k;i++) leftsum+=cardPoints[i];`
        `maxi=leftsum;`
        `int rightindex=cardPoints.length-1;`
        `for(int i=k-1;i>=0;i--){`
            `rightsum+=cardPoints[rightindex];`
            `leftsum-=cardPoints[i];`
            `rightindex--;`
            `maxi=Math.max(maxi,rightsum+leftsum);`
        `}`
        `return maxi;`
    `}`
`}`

