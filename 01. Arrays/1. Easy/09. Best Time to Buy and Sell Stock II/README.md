# [122. Best Time to Buy and Sell Stock II (Easy)](https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii/)

<p>Say you have an array for which the <em>i</em><sup>th</sup> element is the price of a given stock on day <em>i</em>.</p>

<p>Design an algorithm to find the maximum profit. You may complete as many transactions as you like (i.e., buy one and sell one share of the stock multiple times).</p>

<p><strong>Note:</strong> You may not engage in multiple transactions at the same time (i.e., you must sell the stock before you buy again).</p>

<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> [7,1,5,3,6,4]
<strong>Output:</strong> 7
<strong>Explanation:</strong> Buy on day 2 (price = 1) and sell on day 3 (price = 5), profit = 5-1 = 4.
&nbsp;            Then buy on day 4 (price = 3) and sell on day 5 (price = 6), profit = 6-3 = 3.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> [1,2,3,4,5]
<strong>Output:</strong> 4
<strong>Explanation:</strong> Buy on day 1 (price = 1) and sell on day 5 (price = 5), profit = 5-1 = 4.
&nbsp;            Note that you cannot buy on day 1, buy on day 2 and sell them later, as you are
&nbsp;            engaging multiple transactions at the same time. You must sell before buying again.
</pre>

<p><strong>Example 3:</strong></p>

<pre><strong>Input:</strong> [7,6,4,3,1]
<strong>Output:</strong> 0
<strong>Explanation:</strong> In this case, no transaction is done, i.e. max profit = 0.</pre>


**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Uber](https://leetcode.com/company/uber), [Facebook](https://leetcode.com/company/facebook), [Google](https://leetcode.com/company/google), [Adobe](https://leetcode.com/company/adobe), [Microsoft](https://leetcode.com/company/microsoft)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Greedy](https://leetcode.com/tag/greedy/)

## Video Notes

![vlcsnap-2022-06-08-16h31m10s828](https://user-images.githubusercontent.com/37560890/172604833-e0c799b4-d474-4232-b970-f75d47575ed5.png)
![vlcsnap-2022-06-08-16h34m01s671](https://user-images.githubusercontent.com/37560890/172604844-f1d9be82-36f0-4293-8dc8-8f1bad76f1fc.png)
![vlcsnap-2022-06-08-16h37m29s167](https://user-images.githubusercontent.com/37560890/172604849-105821a3-18c1-422d-90b4-12c11a495cf6.png)
![vlcsnap-2022-06-08-16h38m31s355](https://user-images.githubusercontent.com/37560890/172604854-69de74f9-0dc3-45fe-b60b-306569a90d83.png)
![vlcsnap-2022-06-08-16h39m02s434](https://user-images.githubusercontent.com/37560890/172604862-c32862ce-febb-4a72-a6d7-045ce8ef616d.png)
![vlcsnap-2022-06-08-16h39m16s253](https://user-images.githubusercontent.com/37560890/172604930-cd01b6ca-1030-4544-be58-7dd533f7536b.png)
![vlcsnap-2022-06-08-16h41m33s642](https://user-images.githubusercontent.com/37560890/172604988-3295a1fb-5cda-4f9d-9eb6-363ba695e891.png)
![vlcsnap-2022-06-08-16h43m18s460](https://user-images.githubusercontent.com/37560890/172604998-ed4f0215-efd1-467d-8183-d0f912a26c50.png)
![vlcsnap-2022-06-08-16h43m38s810](https://user-images.githubusercontent.com/37560890/172605018-a7eb32f2-a0ff-4c0b-ba12-24b2aa9d0592.png)
![vlcsnap-2022-06-08-16h44m26s142](https://user-images.githubusercontent.com/37560890/172605035-5f87fca3-a229-43d7-8cb6-703b244211f9.png)
![vlcsnap-2022-06-08-16h45m32s759](https://user-images.githubusercontent.com/37560890/172605049-1a02f1ed-3024-41e5-b889-14a65d26cad6.png)
![vlcsnap-2022-06-08-16h45m42s347](https://user-images.githubusercontent.com/37560890/172605072-dd4dfccc-a59b-4a92-8cef-ff947fe271ad.png)
![vlcsnap-2022-06-08-16h46m07s305](https://user-images.githubusercontent.com/37560890/172605085-1cde0806-7188-45ae-8521-490c274970b7.png)

![image](https://user-images.githubusercontent.com/37560890/172605627-7685bb70-eea0-48df-b1b4-bab0e962f4e9.png)


## Solution 1.

```cpp
// OJ: https://leetcode.com/problems/best-time-to-buy-and-sell-stock-ii
// Time: O(N)
// Space: O(1)

class Solution 
{
public:
    int maxProfit(vector<int>& prices) 
    {
        int ans = 0;
        for (int i = 1; i < prices.size(); ++i) 
		ans += max(prices[i] - prices[i - 1], 0);
        return ans;
    }
};

```

## Solution 2.

```cpp
// Time: O(N)
// Space: O(1)

class Solution 
{
public:
    int maxProfit(vector<int>& prices) 
    {
        // For optimization of input and output operation
        ios_base::sync_with_stdio(false);
        cin.tie(NULL);
        
        // Compute the prices array size
        int n= prices.size();
        int profit =0;
        
        // Iterate through the array
        for(int i=1;i<n;i++)
        {
            if(prices[i]>prices[i-1])
            {
                profit= profit+prices[i]-prices[i-1];
            }
        }
        
        // Return the profit
        return profit;
    }
};
```
