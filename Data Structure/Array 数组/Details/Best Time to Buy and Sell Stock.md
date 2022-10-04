# You are given an array prices where prices[i] is the price of a given stock on the ith day.

<p>You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return 0.
</p>

<p>贪心算法：对于每一天的价格，考虑在那天之前的最低价买入，看是否能更新答案</p>

### Example 1

```
Input: prices = [7,1,5,3,6,4]
Output: 5
Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.
Note that buying on day
```
### Example 2
```
Input: prices = [7,6,4,3,1]
Output: 0
Explanation: In this case, no transactions are done and the max profit = 0.
```
### Constraints:
```
1 <= prices.length <= 105
0 <= prices[i] <= 104
```
### Method 1 : Bruto Force
<p>Two pointers, one is i, the other is j (j = i+1), iterate all the possibility, and save the max difference</p>

#### Time O(n²); 超时了，Loop runs (n(n-1))/2 times.
#### Space O(1); 

<br>

### Method 2 : Greedy
<p>Loop once using for each, at the same time, update the min price, and max profit</p>

```
class Solution {
    public int maxProfit(int[] prices) {
        int minPrice = Integer.MAX_VALUE;
        int maxProfit = 0;
        for (int i : prices) {
            minPrice = minPrice > i ? i : minPrice;
            maxProfit = i - minPrice > maxProfit ? i - minPrice : maxProfit;
        }
        return maxProfit;
        
    }
}

```
<br>
<p>Normal Expression (using if/else)</p>

```
public class Solution {
    public int maxProfit(int prices[]) {
        int minprice = Integer.MAX_VALUE;
        int maxprofit = 0;
        for (int i = 0; i < prices.length; i++) {
            if (prices[i] < minprice)
                minprice = prices[i];
            else if (prices[i] - minprice > maxprofit)
                maxprofit = prices[i] - minprice;
        }
        return maxprofit;
    }
}
```

#### Time O(n); 
#### Space O(1); 

