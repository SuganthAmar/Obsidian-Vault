[76. Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/)

Given two strings `s` and `t` of lengths `m` and `n` respectively, return _the **minimum window**_ 

**_substring_**

 _of_ `s` _such that every character in_ `t` _(**including duplicates**) is included in the window_. If there is no such substring, return _the empty string_ `""`.

The testcases will be generated such that the answer is **unique**.

**Example 1:**

**Input:** s = "ADOBECODEBANC", t = "ABC"
**Output:** "BANC"
**Explanation:** The minimum window substring "BANC" includes 'A', 'B', and 'C' from string t.

![[Pasted image 20240403180044.png]]

**Edge Case**

![[Pasted image 20240403180138.png]]

## Brute Force
![[Pasted image 20240403180955.png]]
![[Pasted image 20240403181059.png]]
