# [121. Best Time to Buy and Sell Stock (Easy)](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)

<p>Say you have an array for which the <em>i</em><sup>th</sup> element is the price of a given stock on day <em>i</em>.</p>

<p>If you were only permitted to complete at most one transaction (i.e., buy one and sell one share of the stock), design an algorithm to find the maximum profit.</p>

<p>Note that you cannot sell a stock before you buy one.</p>

<p><strong>Example 1:</strong></p>

<pre><strong>Input:</strong> [7,1,5,3,6,4]
<strong>Output:</strong> 5
<strong>Explanation:</strong> Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
&nbsp;            Not 7-1 = 6, as selling price needs to be larger than buying price.
</pre>

<p><strong>Example 2:</strong></p>

<pre><strong>Input:</strong> [7,6,4,3,1]
<strong>Output:</strong> 0
<strong>Explanation:</strong> In this case, no transaction is done, i.e. max profit = 0.
</pre>


**Companies**:  
[Amazon](https://leetcode.com/company/amazon), [Facebook](https://leetcode.com/company/facebook), [Microsoft](https://leetcode.com/company/microsoft), [Google](https://leetcode.com/company/google), [Apple](https://leetcode.com/company/apple), [Goldman Sachs](https://leetcode.com/company/goldman-sachs), [DoorDash](https://leetcode.com/company/doordash), [Adobe](https://leetcode.com/company/adobe), [Morgan Stanley](https://leetcode.com/company/morgan-stanley), [Citadel](https://leetcode.com/company/citadel), [Walmart Labs](https://leetcode.com/company/walmart-labs), [VMware](https://leetcode.com/company/vmware), [Redfin](https://leetcode.com/company/redfin)

**Related Topics**:  
[Array](https://leetcode.com/tag/array/), [Dynamic Programming](https://leetcode.com/tag/dynamic-programming/)


## Video Notes

![vlcsnap-2022-06-06-21h18m00s284](https://user-images.githubusercontent.com/37560890/172199242-e92db74a-22a9-453f-b845-72088d7c4e63.png)
![vlcsnap-2022-06-06-21h18m02s514](https://user-images.githubusercontent.com/37560890/172199247-2404ebf9-7dbb-4a43-84ae-50d1d3454677.png)
![vlcsnap-2022-06-06-21h20m40s406](https://user-images.githubusercontent.com/37560890/172199248-1bddf3f5-1d02-41fe-b60f-b1fcd580bf68.png)
![vlcsnap-2022-06-06-21h20m57s346](https://user-images.githubusercontent.com/37560890/172199252-003a00fe-f2b8-4cdb-81b0-07793e9b5c25.png)
![vlcsnap-2022-06-06-21h21m03s596](https://user-images.githubusercontent.com/37560890/172199254-9818e9de-80e6-48d9-9065-efb98b878ea0.png)
![vlcsnap-2022-06-06-21h24m31s495](https://user-images.githubusercontent.com/37560890/172199256-60eb2d88-f085-4e8a-a63f-c71117f1334a.png)
![vlcsnap-2022-06-06-21h24m38s270](https://user-images.githubusercontent.com/37560890/172199258-f92fb9a1-4473-4f7d-a26e-e1c1cbd5ac55.png)



## Solution 1.

```cpp
// OJ: https://leetcode.com/problems/best-time-to-buy-and-sell-stock
// Time: O(N)
// Space: O(1)

class Solution 
{
public:
    int maxProfit(vector<int>& prices) 
    {
        // Initialize the variable's
        int mini_price= INT_MAX;
        int max_profit= 0;
        
        // Iterate over the profit array
        for(int i=0;i<prices.size();i++)
        {
            // Updat the min price and max_profit
            mini_price= min(prices[i], mini_price);
            max_profit= max(max_profit, prices[i]-mini_price);
        }
        
        // Finally return th max profit
        return max_profit;
    }
};
```
