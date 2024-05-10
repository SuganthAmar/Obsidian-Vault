## Pattern -1 -Constant Window 
![[Pasted image 20240329102906.png]]

**Given the array and the window sum need to find the maximum sum of the window size and return the size** 
![[Pasted image 20240329103010.png]]

The window ends at the (r), when reaches the n-1 position the loop ends so at every step we need to add the new r'th element to sum and when the window size is moved we need to subract the l'th element to the sum to maintain the window size 

![[Pasted image 20240329103047.png]]

Step -1 : Run a loop from l=0 to K the window size is set to r 0 to 4 is the initial sum and the window position then move to next l++ and and r++ and sum-l and sum+r
Step -2 : Start the while loop til the r reaches to the n-1 position
Step -3 : Add this to the sum and subtract the l from sum and add the r to the sum at the array

## Pattern 2 - Longest subarray/substring where `<Condition>`

### Example :
![[Pasted image 20240329104137.png]]

**1)Brute Force**
Generate All possible subarrays

![[Pasted image 20240329105246.png]]

Slight optimisation
2+5+1+7=15 it increases from the k so we don't need to go next after this so break

**2) Better One - Two-Pointer 
![[Pasted image 20240329105903.png]]

window size = `r-l+1`

![[Pasted image 20240329110059.png]]

that is when the sum > k
we need to shrink the window
this can be used when they ask to find the subarray itself

![[Pasted image 20240329110444.png]]

Step 1 : Start the loop and iterate over the length less then n
Step 2 : Add this to the sum that is at the r'th position 
Step 3 : If it exceeds the k keep shrinking using the while
Step 4 : Find the max length and increment the r position

![[Pasted image 20240329110913.png]]

Taking the max length O(n)
Shrinking also O(n)

**optimal Fix Size**
![[Pasted image 20240329111609.png]]
This can be used when we only need the size of the subarray

### 3) No.of subarray where `<Condition>`

