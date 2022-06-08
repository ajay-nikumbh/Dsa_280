# [73. Set Matrix Zeroes (Medium)](https://leetcode.com/problems/set-matrix-zeroes/)

<p>Given an <code>m x n</code> integer matrix <code>matrix</code>, if an element is <code>0</code>, set its entire row and column to <code>0</code>'s, and return <em>the matrix</em>.</p>

<p>You must do it <a href="https://en.wikipedia.org/wiki/In-place_algorithm" target="_blank">in place</a>.</p>

<p>&nbsp;</p>
<p><strong>Example 1:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/08/17/mat1.jpg" style="width: 450px; height: 169px;">
<pre><strong>Input:</strong> matrix = [[1,1,1],[1,0,1],[1,1,1]]
<strong>Output:</strong> [[1,0,1],[0,0,0],[1,0,1]]
</pre>

<p><strong>Example 2:</strong></p>
<img alt="" src="https://assets.leetcode.com/uploads/2020/08/17/mat2.jpg" style="width: 450px; height: 137px;">
<pre><strong>Input:</strong> matrix = [[0,1,2,0],[3,4,5,2],[1,3,1,5]]
<strong>Output:</strong> [[0,0,0,0],[0,4,5,0],[0,3,1,0]]
</pre>

<p>&nbsp;</p>
<p><strong>Constraints:</strong></p>

<ul>
	<li><code>m == matrix.length</code></li>
	<li><code>n == matrix[0].length</code></li>
	<li><code>1 &lt;= m, n &lt;= 200</code></li>
	<li><code>-2<sup>31</sup> &lt;= matrix[i][j] &lt;= 2<sup>31</sup> - 1</code></li>
</ul>

<p>&nbsp;</p>
<p><strong>Follow up:</strong></p>

<ul>
	<li>A straightforward solution using <code>O(mn)</code> space is probably a bad idea.</li>
	<li>A simple improvement uses <code>O(m + n)</code> space, but still not the best solution.</li>
	<li>Could you devise a constant space solution?</li>
</ul>


**Companies**:  
[Microsoft](https://leetcode.com/company/microsoft), [Facebook](https://leetcode.com/company/facebook), [Amazon](https://leetcode.com/company/amazon), [Qualtrics](https://leetcode.com/company/qualtrics)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Hash Table](https://leetcode.com/tag/hash-table/), [Matrix](https://leetcode.com/tag/matrix/)

**Similar Questions**:
* [Game of Life (Medium)](https://leetcode.com/problems/game-of-life/)

## Video Notes

![vlcsnap-2022-06-08-12h32m21s492](https://user-images.githubusercontent.com/106215989/172574528-a00a4a69-7cf9-4e32-b6d5-bbc0846d64bb.png)
![vlcsnap-2022-06-08-12h34m15s080](https://user-images.githubusercontent.com/106215989/172574537-c5be2747-d406-4a92-8528-fd9f8acc622c.png)
![vlcsnap-2022-06-08-12h34m31s410](https://user-images.githubusercontent.com/106215989/172574544-1418492e-f491-467e-ae56-2c3e0774d517.png)
![vlcsnap-2022-06-08-12h36m38s255](https://user-images.githubusercontent.com/106215989/172574548-d168ce8b-b7d8-4fb0-a824-ccfa7ab3c8b4.png)
![vlcsnap-2022-06-08-12h36m49s605](https://user-images.githubusercontent.com/106215989/172574550-4b5869ed-7a4f-4d48-83b2-ee996a95876e.png)
![vlcsnap-2022-06-08-12h36m54s939](https://user-images.githubusercontent.com/106215989/172574556-b9d59a45-df36-4214-a74e-c5ea485e04ab.png)
![vlcsnap-2022-06-08-12h38m40s675](https://user-images.githubusercontent.com/106215989/172574559-7656012d-1128-4756-9e6c-159700d786fa.png)
![vlcsnap-2022-06-08-12h41m09s576](https://user-images.githubusercontent.com/106215989/172574566-3c6b9103-8ec1-4233-b3ee-fe233fa55731.png)
![vlcsnap-2022-06-08-12h42m13s612](https://user-images.githubusercontent.com/106215989/172574572-8e1b5549-87f8-4ca2-abcd-718b643692bf.png)
![vlcsnap-2022-06-08-12h43m27s881](https://user-images.githubusercontent.com/106215989/172574575-bca5043d-b6db-48dc-834a-8ec692ce3658.png)
![vlcsnap-2022-06-08-12h43m47s521](https://user-images.githubusercontent.com/106215989/172574578-c2521355-2aa0-4966-b925-e466ec55b72e.png)
![vlcsnap-2022-06-08-12h44m22s296](https://user-images.githubusercontent.com/106215989/172574581-2c9cffde-8dd0-416d-9760-d853477e32ca.png)
![vlcsnap-2022-06-08-12h44m32s328](https://user-images.githubusercontent.com/106215989/172574584-c8508413-4c16-4190-b81f-d4abf9918fe5.png)
![vlcsnap-2022-06-08-12h45m15s510](https://user-images.githubusercontent.com/106215989/172574588-587ab30a-c8d1-418f-8998-1e03b1548536.png)
![vlcsnap-2022-06-08-12h45m18s203](https://user-images.githubusercontent.com/106215989/172574593-27d3e6c6-e80e-4744-a979-b364e4edcc95.png)
![vlcsnap-2022-06-08-12h45m29s350](https://user-images.githubusercontent.com/106215989/172574597-42b7649f-ca55-46b3-b8c4-22a8a5d0e6b7.png)



## Solution 1.

```cpp
// OJ: https://leetcode.com/problems/set-matrix-zeroes/
// Time: O(MN)
// Space: O(M + N)

class Solution 
{
public:
    void setZeroes(vector<vector<int>>& A) 
    {
        int M = A.size(), N = A[0].size();
        vector<bool> row(M), col(N);
        
	for (int i = 0; i < M; ++i) 
	{
            for (int j = 0; j < N; ++j) 
	    {
                row[i] = row[i] || A[i][j] == 0;
                col[j] = col[j] || A[i][j] == 0;
            }
        }
        
	for (int i = 0; i < M; ++i) 
	{
            for (int j = 0; j < N; ++j) 
	    {
                if (row[i] || col[j]) A[i][j] = 0;
            }
        }
    }
};
```

## Solution 2.

```cpp
class Solution 
{
public:
    void setZeroes(vector<vector<int>>& matrix) 
    {
        // Compute the rows and cols size
        int rows= matrix.size();
        int cols= matrix[0].size();
        int col0= 1;
        
        for(int i=0;i<rows;i++)
        {
            // Condition checking for col
            if(matrix[i][0]==0) col0=0;
            
            // Travel for cols
            for(int j=1;j<cols;j++)
            {
                
                // If the ele is 0 keep as it is
                if(matrix[i][j]==0)
                {
                    matrix[i][0] = matrix[0][j]=0;
                }
            }
        }
        
        // Travel from the backward direction
        for(int i=rows-1; i>=0 ; i--)
        {
            for(int j=cols-1;j>=1; j--)
            {
                // If any of the rows or cols is set to 0 then set entire col & row 0
                if(matrix[i][0]==0 or matrix[0][j]==0)
                {
                    matrix[i][j]=0;
                }
            }
            
            // Check for the col condition
            if(col0==0) matrix[i][0] =0;
        }
        
    }
};
```
