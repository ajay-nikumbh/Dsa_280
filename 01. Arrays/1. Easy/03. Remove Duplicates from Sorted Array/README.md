# [26. Remove Duplicates from Sorted Array (Easy)](https://leetcode.com/problems/remove-duplicates-from-sorted-array/)

<p>Given a sorted array <em>nums</em>, remove the duplicates <a href="https://en.wikipedia.org/wiki/In-place_algorithm" target="_blank"><strong>in-place</strong></a> such that each element appears only <em>once</em> and returns the new length.</p>

<p>Do not allocate extra space for another array, you must do this by <strong>modifying the input array <a href="https://en.wikipedia.org/wiki/In-place_algorithm" target="_blank">in-place</a></strong> with O(1) extra memory.</p>

<p><strong>Clarification:</strong></p>

<p>Confused why the returned value is an integer but your answer is an array?</p>

<p>Note that the input array is passed in by <strong>reference</strong>, which means a modification to the input array will be known to the caller as well.</p>

<p>Internally you can think of this:</p>

<pre>// <strong>nums</strong> is passed in by reference. (i.e., without making a copy)
int len = removeDuplicates(nums);

// any modification to <strong>nums</strong> in your function would be known by the caller.
// using the length returned by your function, it prints the first <strong>len</strong> elements.
for (int i = 0; i &lt; len; i++) {
&nbsp; &nbsp; print(nums[i]);
}</pre>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> nums = [1,1,2]
<strong>Output:</strong> 2, nums = [1,2]
<strong>Explanation:</strong>&nbsp;Your function should return length = <strong><code>2</code></strong>, with the first two elements of <em><code>nums</code></em> being <strong><code>1</code></strong> and <strong><code>2</code></strong> respectively. It doesn't matter what you leave beyond the returned length.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> nums = [0,0,1,1,1,2,2,3,3,4]
<strong>Output:</strong> 5, nums = [0,1,2,3,4]
<strong>Explanation:</strong>&nbsp;Your function should return length = <strong><code>5</code></strong>, with the first five elements of <em><code>nums</code></em> being modified to&nbsp;<strong><code>0</code></strong>, <strong><code>1</code></strong>, <strong><code>2</code></strong>, <strong><code>3</code></strong>, and&nbsp;<strong><code>4</code></strong> respectively. It doesn't matter what values are set beyond&nbsp;the returned length.
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>0 &lt;= nums.length &lt;= 3 * 10<sup>4</sup></code></li>
	<li><code>-10<sup>4</sup> &lt;= nums[i] &lt;= 10<sup>4</sup></code></li>
	<li><code>nums</code>&nbsp;is sorted in ascending order.</li>
</ul>


**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Two Pointers](https://leetcode.com/tag/two-pointers/)

**Similar Questions**:
* [Remove Element (Easy)](https://leetcode.com/problems/remove-element/)
* [Remove Duplicates from Sorted Array II (Medium)](https://leetcode.com/problems/remove-duplicates-from-sorted-array-ii/)

## Video Notes

![vlcsnap-2022-06-06-18h01m38s724](https://user-images.githubusercontent.com/37560890/172163852-d6bb214e-68e3-41f9-a12d-7c0490d07ada.png)
![vlcsnap-2022-06-06-18h07m08s480](https://user-images.githubusercontent.com/37560890/172163863-7dced864-8656-4af1-a8a7-f3b837158f6d.png)
![vlcsnap-2022-06-06-18h07m22s594](https://user-images.githubusercontent.com/37560890/172163865-cbda68f7-da80-4f27-80dc-8d9a69bcac06.png)
![vlcsnap-2022-06-06-18h09m51s682](https://user-images.githubusercontent.com/37560890/172163868-49e69041-6fe2-4c12-b45c-70c06063d0d7.png)
![vlcsnap-2022-06-06-18h12m55s379](https://user-images.githubusercontent.com/37560890/172163874-a62f7dff-fb1b-495e-99d2-e621c01d386b.png)
![vlcsnap-2022-06-06-18h13m51s659](https://user-images.githubusercontent.com/37560890/172163878-0f5c9e85-e741-4347-94e0-e0ebb52142ec.png)
![vlcsnap-2022-06-06-18h14m49s170](https://user-images.githubusercontent.com/37560890/172163881-7f80be27-d424-4b57-a502-93d5a37f5aba.png)



## Solution 1.

```cpp
// OJ: https://leetcode.com/problems/remove-duplicates-from-sorted-array/
// Time: O(N)
// Space: O(1)
```cpp
class Solution
{
public:
    int removeDuplicates(vector<int>& nums) 
    {
        nums.erase(unique(nums.begin(), nums.end()) , nums.end());
        return nums.size();
        
    }
};
```

## Solution 2. Two pointer approach

```cpp
// OJ: https://leetcode.com/problems/remove-duplicates-from-sorted-array/
// Time: O(N)
// Space: O(1)

class Solution
{
public:
    int removeDuplicates(vector<int>& nums) 
    {
        // Base checking
        if(nums.size()==0) return 0;
        
        // Using the 2 pointer technique
        
        // Initialize the i variable i.e the pointer 1
        int i=0;
        
        // Initialize the j variable i.e the pointer 2  
        for(int j=1; j<nums.size();j++)
        {
            // If both pointer not equal then do the following given below
            if(nums[i]!=nums[j])
            {
                i++;
                nums[i] = nums[j];
                
            }
        }
        
        // At last return the i+1 as index start's from 0
        return i+1;
    }
};
```

## Solution 3. Using the counting method

```cpp

int count = 0;
for(int i = 1; i < n; i++)
{
    if(A[i] == A[i-1]) count++;
    else A[i-count] = A[i];
}
return n-count;
```



