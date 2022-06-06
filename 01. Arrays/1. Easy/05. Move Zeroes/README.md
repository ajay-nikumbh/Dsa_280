<h2><a href="https://leetcode.com/problems/move-zeroes/">283. Move Zeroes</a></h2><h3>Easy</h3><hr><div><p>Given an integer array <code>nums</code>, move all <code>0</code>'s to the end of it while maintaining the relative order of the non-zero elements.</p>

<p><strong>Note</strong> that you must do this in-place without making a copy of the array.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<pre><strong>Input:</strong> nums = [0,1,0,3,12]
<strong>Output:</strong> [1,3,12,0,0]
</pre><p><strong>Example 2:</strong></p>
<pre><strong>Input:</strong> nums = [0]
<strong>Output:</strong> [0]
</pre>
<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>1 &lt;= nums.length &lt;= 10<sup>4</sup></code></li>
	<li><code>-2<sup>31</sup> &lt;= nums[i] &lt;= 2<sup>31</sup> - 1</code></li>
</ul>

<p>&nbsp;</p>
<strong>Follow up:</strong> Could you minimize the total number of operations done?</div>

## Video Notes

![vlcsnap-2022-06-06-18h32m53s924](https://user-images.githubusercontent.com/37560890/172168467-4e6ad0fb-0e48-4156-9f7d-6b0e0bbbd22f.png)
![vlcsnap-2022-06-06-18h34m58s015](https://user-images.githubusercontent.com/37560890/172168472-e54947e6-1aa9-41a3-b975-157a11fc99b6.png)
![vlcsnap-2022-06-06-18h38m46s051](https://user-images.githubusercontent.com/37560890/172168476-1f304ab4-02be-4445-8a7c-c09481fb9dfc.png)
![vlcsnap-2022-06-06-18h38m59s467](https://user-images.githubusercontent.com/37560890/172168480-fb89e651-e588-4f83-97cf-0b43999876c1.png)
![vlcsnap-2022-06-06-18h40m47s007](https://user-images.githubusercontent.com/37560890/172168483-e0545cc1-a197-47e6-8917-c7a2595a081b.png)
![vlcsnap-2022-06-06-18h42m35s293](https://user-images.githubusercontent.com/37560890/172168485-e9781278-fc7b-46f9-a107-76c7beaf19b4.png)
![vlcsnap-2022-06-06-18h43m07s269](https://user-images.githubusercontent.com/37560890/172168487-853228e6-4b3c-4a11-8fcb-4a801e598b8b.png)
![image](https://user-images.githubusercontent.com/37560890/172169019-f540e11d-a4e6-4949-9e04-8f90e43b789b.png)

## Solution 1. 2 pointer approach

```cpp
class Solution 
{
public:
    void moveZeroes(vector<int>& nums) 
    {
        // Compute the size of the nums
        int n= nums.size();
        
        // If Edge cases then return 
        if(n==0 || n==1) return ;
        
        // Take 2 pointer left and right
        int left=0, right=0;
        
        // Iterate till right < nums.size
        while(right<n)
        {
            // If right is pointing to 0 then skip and incr right pointer
            if(nums[right]==0) 
            {
                right++;
            }
            
            // Else swap the left and right values
            else
            {
                swap(nums[left++], nums[right++]);
            }
        }
    }
};
```

## Solution 2

```cpp
class Solution 
{
public:
    void moveZeroes(vector<int>& nums) 
    {
        int j = 0;
        // move all the nonzero elements advance
        for (int i = 0; i < nums.size(); i++) 
	{
            if (nums[i] != 0) 
	    {
                nums[j++] = nums[i];
            }
        }
        
	for (;j < nums.size(); j++) 
	{
            nums[j] = 0;
        }
    }
};
```
