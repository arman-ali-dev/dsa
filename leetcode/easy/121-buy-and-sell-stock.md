# Best Time to Buy and Sell Stock

## Problem
We are given an array prices where:
- prices[i] = stock price on day i.
We need to find the maximum profit we can get by:
- Choosing one day to buy the stock.
- Choosing a later day to sell the stock.
- You must buy before selling.
- If no profit is possible, return 0.

### Example 1
```ini
prices = [7,1,5,3,6,4]
```
- Buy on day 2 (price = 1)
- Sell on day 5 (price = 6)
- Profit = 6 - 1 = 5
- Output - 5

### Example 2

```ini
prices = [7,6,4,3,1]
```
- Here, prices are always going down.
- So, no profit is possible.
- Output - 0

## Idea / Intuition
We want to buy at the lowest price and sell at the highest price after that.<br/>
</br>

So we keep track of:
- The minimum price seen so far (bestBuy).
- The maximum profit possible till now.

--- 

## Approach (Step by Step)
1. Start with:
    - bestBuy = prices[0]
    - maxProfit = 0

2. Traverse the array from day 1 to end:
    - If today’s price > bestBuy → calculate profit = price - bestBuy
    - Update maxProfit if this profit is bigger.
    - Otherwise update bestBuy = min(bestBuy, price).

3. At the end, return maxProfit.

### Dry Run (Example: [7,1,5,3,6,4])

- Start: bestBuy = 7, maxProfit = 0
- Day 1 → price=1 → update bestBuy=1
- Day 2 → price=5 → profit=4 → update maxProfit=4
- Day 3 → price=3 → profit=2 → maxProfit=4
- Day 4 → price=6 → profit=5 → update maxProfit=5
- Day 5 → price=4 → profit=3 → maxProfit=5
- Final Answer = 5

### Code

```c++
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int maxProfit = 0;
        int bestBuy = prices[0]; // minimum price so far

        for(int i = 1; i < prices.size(); i++) {
            if(prices[i] > bestBuy) {
                // profit possible
                maxProfit = max(maxProfit, prices[i] - bestBuy);
            }
            // update bestBuy if today’s price is lower
            bestBuy = min(bestBuy, prices[i]);
        }
        return maxProfit;
    }
};
```


## Complexity
- **Time Complexity: O(n)** → We scan the array once.
- **Space Complexity: O(1)** → Only a few variables are used.
