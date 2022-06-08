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
