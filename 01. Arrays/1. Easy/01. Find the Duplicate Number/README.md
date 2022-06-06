# [287. Find the Duplicate Number (Medium)](https://leetcode.com/problems/find-the-duplicate-number/)

<p>Given an array of integers <code>nums</code> containing&nbsp;<code>n + 1</code> integers where each integer is in the range <code>[1, n]</code> inclusive.</p>

<p>There is only <strong>one repeated number</strong> in <code>nums</code>, return <em>this&nbsp;repeated&nbsp;number</em>.</p>

<p>You must solve the problem <strong>without</strong> modifying the array <code>nums</code>&nbsp;and uses only constant extra space.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> nums = [1,3,4,2,2]
<strong>Output:</strong> 2
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> nums = [3,1,3,4,2]
<strong>Output:</strong> 3
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= n &lt;= 10<sup>5</sup></code></li>
	<li><code>nums.length == n + 1</code></li>
	<li><code>1 &lt;= nums[i] &lt;= n</code></li>
	<li>All the integers in <code>nums</code> appear only <strong>once</strong> except for <strong>precisely one integer</strong> which appears <strong>two or more</strong> times.</li>
</ul>

<p>&nbsp;</p>
<p><b>Follow up:</b></p>

<ul>
	<li>How can we prove that at least one duplicate number must exist in <code>nums</code>?</li>
	<li>Can you solve the problem in linear runtime complexity?</li>
</ul>


**Companies**:  
[Microsoft](https://leetcode.com/company/microsoft), [Amazon](https://leetcode.com/company/amazon), [Facebook](https://leetcode.com/company/facebook), [Apple](https://leetcode.com/company/apple), [Google](https://leetcode.com/company/google)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Two Pointers](https://leetcode.com/tag/two-pointers/), [Binary Search](https://leetcode.com/tag/binary-search/), [Bit Manipulation](https://leetcode.com/tag/bit-manipulation/)

**Similar Questions**:
* [First Missing Positive (Hard)](https://leetcode.com/problems/first-missing-positive/)
* [Single Number (Easy)](https://leetcode.com/problems/single-number/)
* [Linked List Cycle II (Medium)](https://leetcode.com/problems/linked-list-cycle-ii/)
* [Missing Number (Easy)](https://leetcode.com/problems/missing-number/)
* [Set Mismatch (Easy)](https://leetcode.com/problems/set-mismatch/)

## Video Notes 

![vlcsnap-2022-06-06-13h05m42s751](https://user-images.githubusercontent.com/37560890/172123513-da59f214-f95a-4c0b-8abe-41f9a172acec.png)
![vlcsnap-2022-06-06-13h06m52s929](https://user-images.githubusercontent.com/37560890/172123527-b5554f08-0e6f-44cb-a62c-2e75f026b31d.png)
![vlcsnap-2022-06-06-13h12m43s732](https://user-images.githubusercontent.com/37560890/172123532-bcd15cfe-75c0-4a12-b2a0-f2ab4a319e9e.png)
![vlcsnap-2022-06-06-13h16m02s867](https://user-images.githubusercontent.com/37560890/172123536-3dba4297-e2cd-40db-b3ef-3a5d61793247.png)
![vlcsnap-2022-06-06-13h20m26s555](https://user-images.githubusercontent.com/37560890/172123539-40aa9aa5-0975-4990-9c06-be261b330f72.png)
![vlcsnap-2022-06-06-13h20m28s325](https://user-images.githubusercontent.com/37560890/172123540-5626f496-79c0-4e3c-8eca-1313ebc03ac1.png)
![vlcsnap-2022-06-06-13h21m40s752](https://user-images.githubusercontent.com/37560890/172123544-76f84d55-6e82-44f3-94d3-e0d97c3ef2fd.png)
![vlcsnap-2022-06-06-13h25m39s024](https://user-images.githubusercontent.com/37560890/172123551-d144c514-4cf2-4265-99c5-21927208702f.png)
![vlcsnap-2022-06-06-13h26m37s562](https://user-images.githubusercontent.com/37560890/172123554-257f5e1b-0cd4-431b-a0f3-50319f2d42b4.png)
![vlcsnap-2022-06-06-13h27m01s821](https://user-images.githubusercontent.com/37560890/172123558-a757062e-2627-4543-9b02-8b7a98cd7b06.png)
![vlcsnap-2022-06-06-13h27m14s909](https://user-images.githubusercontent.com/37560890/172123563-e8ea6caf-3e3a-4371-95a4-d9aed5b232d3.png)


## Solution 1. Binary Search

Numbers less than the duplicate number must have frequencies less than or equal to themselves.

Examples:

* `A = [1 2 3 3 4]`, `1,2` have frequencies (`1,2`) less than or equal to themselves.
* `A = [3 2 3 3 4]`, `1,2` have frequencies (`0,1`) less than or equal to themselves. 

`L < R` template:

* Range: `[1, A.size()-1]` 
* Let `cnt` be the count of numbers less than or equal to `M`. If `cnt <= M`, the duplicate number is greater than `M`, so `L = M + 1`; otherwise, `R = M`.

```cpp
// OJ: https://leetcode.com/problems/find-the-duplicate-number/
// Time: O(NlogN)
// Space: O(1)

class Solution 
{
public:
    int findDuplicate(vector<int>& A) 
    {
        int L = 1, R = A.size() - 1;
        while (L < R) 
	{
            int M = (L + R) / 2, cnt = 0;
            for (int n : A) cnt += n <= M;
            if (cnt <= M) L = M + 1;
            else R = M;
        }
        return L;
    }
};
```

`L <= R` template:

* Range: `[1, A.size()-1]`.
* Let `cnt` be the count of numbers less than or equal to `M`. The answer is the first number that `cnt > ` itself. So, we return `L` in the end.

```cpp
// OJ: https://leetcode.com/problems/find-the-duplicate-number/
// Time: O(NlogN)
// Space: O(1)

class Solution 
{
public:
    int findDuplicate(vector<int>& A) 
    {
        int L = 1, R = A.size() - 1;
        while (L <= R) 
	{
            int M = (L + R) / 2, cnt = 0;
            for (int n : A) cnt += n <= M;
            if (cnt <= M) L = M + 1;
            else R = M - 1;
        }
        return L;
    }
};
```

## Solution 2. Floyd's Tortoise and Hare (Cycle Detection)

```cpp
// OJ: https://leetcode.com/problems/find-the-duplicate-number/
// Time: O(N)
// Space: O(1)

class Solution 
{
public:
   int floydSolution(vector<int>& nums) 
   {
        // Each index is taken 1 based, as if it is zero based, then
        // for nums[2] = 3, if we goto nums[nums[2] - 1], it is again nums[2]
        // infinite loop
        int hare = nums[0], tortoise = nums[0];
        
        do {
            hare = nums[nums[hare]];
            tortoise = nums[tortoise];
        } while(hare != tortoise);
        
        // to find the starting of cycle, make tortoise to start from begining
        tortoise = nums[0];
        
       while(hare != tortoise) 
       {
            hare = nums[hare];
            tortoise = nums[tortoise];
       }
       return hare;
    }
    
    int findDuplicate(vector<int>& nums) 
    {
        return floydSolution(nums);
        
    }
};
```
