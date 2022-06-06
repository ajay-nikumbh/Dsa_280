# [75. Sort Colors (Medium)](https://leetcode.com/problems/sort-colors/)

<p>Given an array <code>nums</code> with <code>n</code> objects colored red, white, or blue, sort them <strong><a href="https://en.wikipedia.org/wiki/In-place_algorithm" target="_blank">in-place</a> </strong>so that objects of the same color are adjacent, with the colors in the order red, white, and blue.</p>

<p>We will use the integers <code>0</code>, <code>1</code>, and <code>2</code> to represent the color red, white, and blue, respectively.</p>

<p>You must solve this problem without using the library's sort function.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> nums = [2,0,2,1,1,0]
<strong>Output:</strong> [0,0,1,1,2,2]
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> nums = [2,0,1]
<strong>Output:</strong> [0,1,2]
</pre><p><strong>Example 3:</strong></p>
<pre><strong>Input:</strong> nums = [0]
<strong>Output:</strong> [0]
</pre><p><strong>Example 4:</strong></p>
<pre><strong>Input:</strong> nums = [1]
<strong>Output:</strong> [1]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>n == nums.length</code></li>
	<li><code>1 &lt;= n &lt;= 300</code></li>
	<li><code>nums[i]</code> is <code>0</code>, <code>1</code>, or <code>2</code>.</li>
</ul>

<p>&nbsp;</p>
<p><strong>Follow up:</strong>&nbsp;Could you come up with a one-pass algorithm using only&nbsp;constant extra space?</p>


**Companies**:  
[Microsoft](https://leetcode.com/company/microsoft), [Amazon](https://leetcode.com/company/amazon), [Adobe](https://leetcode.com/company/adobe), [Apple](https://leetcode.com/company/apple), [Facebook](https://leetcode.com/company/facebook), [Bloomberg](https://leetcode.com/company/bloomberg), [Nvidia](https://leetcode.com/company/nvidia), [Swiggy](https://leetcode.com/company/swiggy)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Two Pointers](https://leetcode.com/tag/two-pointers/), [Sorting](https://leetcode.com/tag/sorting/)

**Similar Questions**:
* [Sort List (Medium)](https://leetcode.com/problems/sort-list/)
* [Wiggle Sort (Medium)](https://leetcode.com/problems/wiggle-sort/)
* [Wiggle Sort II (Medium)](https://leetcode.com/problems/wiggle-sort-ii/)

## Video Notes

![vlcsnap-2022-06-06-14h15m49s135](https://user-images.githubusercontent.com/37560890/172131685-26b3a466-397f-431e-bb20-93138105d38a.png)
![vlcsnap-2022-06-06-14h17m27s945](https://user-images.githubusercontent.com/37560890/172131709-9f5c7cd3-5864-47ac-8835-75573f67b9bb.png)
![vlcsnap-2022-06-06-14h18m37s149](https://user-images.githubusercontent.com/37560890/172131716-20b48cea-13a1-42ad-8c80-8fe3a378b363.png)
![vlcsnap-2022-06-06-14h20m14s570](https://user-images.githubusercontent.com/37560890/172131720-58ea4ec8-5d09-40df-9dc3-15c991963db8.png)
![vlcsnap-2022-06-06-14h20m40s203](https://user-images.githubusercontent.com/37560890/172131722-f8fd9e7a-003b-45f6-b0ef-34792d0e9a7a.png)
![vlcsnap-2022-06-06-14h23m30s000](https://user-images.githubusercontent.com/37560890/172131725-61cf5b03-7e32-4b43-8d5b-e8e43ffcdda1.png)
![vlcsnap-2022-06-06-14h25m03s853](https://user-images.githubusercontent.com/37560890/172131729-617d43af-8760-410c-8da3-fdb8fb0ad9eb.png)
![vlcsnap-2022-06-06-14h25m36s721](https://user-images.githubusercontent.com/37560890/172131733-b34acd4f-2959-4309-b9ac-94a91784b151.png)
![vlcsnap-2022-06-06-14h26m08s396](https://user-images.githubusercontent.com/37560890/172131739-69fd3e3f-cac0-4b95-a44e-e4d89b4578bf.png)
![vlcsnap-2022-06-06-14h26m17s169](https://user-images.githubusercontent.com/37560890/172131745-83908c9d-bfe6-4799-ac2c-288f99beceac.png)


![image](https://user-images.githubusercontent.com/37560890/172131576-eda1a869-84cc-4ab4-990e-20b10455f051.png)
![image](https://user-images.githubusercontent.com/37560890/172131627-84f8cd2f-2804-42f5-b00d-f9f16091bdff.png)


## Solution

[Dutch national flag problem](https://en.wikipedia.org/wiki/Dutch_national_flag_problem)

```cpp
// OJ: https://leetcode.com/problems/sort-colors/
// Time: O(N)
// Space: O(1)

class Solution
{
public:
    void sortColors(vector<int>& nums) 
    {
        // Initialize the low
        int low= 0;
        
        // Initialize the mid
        int mid= 0;
        
        // Initialize the high
        int high = nums.size()-1;
        
        // Iterate till mid <= high
        while(mid<=high)
        {
            // Switch the mid and check the cases
            switch(nums[mid])
            {
                // If the element is 0
                case 0: swap(nums[low++],nums[mid++]); break;
                
                // If the element is 1
                case 1: mid++; break;
                
                // If the element is 2
                case 2: swap(nums[mid],nums[high--]); break;
            }
        }
    }
};
```
