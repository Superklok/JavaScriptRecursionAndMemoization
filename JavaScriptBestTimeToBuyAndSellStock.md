# JavaScript Best Time to Buy and Sell Stock
<br/>

## Challenge
You are given an array `prices` where `prices[i]` is the price of a given stock on the `iᵗʰ` day.

You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.

Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return `0`.
<br/>
<br/>

### 1<sup>st</sup> Example

```JavaScript
Input: prices = [7,1,5,3,6,4]
Output: 5
Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6),
             profit = 6-1 = 5. Note that buying on day 2 and selling on day 1
             is not allowed because you must buy before you sell.
```

### 2<sup>nd</sup> Example

```JavaScript
Input: prices = [7,6,4,3,1]
Output: 0
Explanation: In this case, no transactions are done and the max profit = 0.
```

<br/>

### Constraints

```JavaScript
1 <= prices.length <= 10⁵
0 <= prices[i] <= 10⁴
```

<br/>

## Solution

```JavaScript
const maxProfit = (prices) => {
    let max   = 0,
        left  = 0,
        right = 1;

    while (right < prices.length) {
        const profit = prices[right] - prices[left];

        if (profit > max) {
            max = profit;
        }

        if (profit < 0) {
            left = right;
        }

        right += 1;
    }

    return max;
};
```

<br/>

## Explanation

I've built a function called `maxProfit` that calculates the maximum profit that can be made by buying and selling a stock at different prices.
<br/>

Inside the function, three variables are initialized: `max` (representing the maximum profit), `left` (representing the index of the lowest buying price), and `right` (representing the index of the selling price).
<br/>

The function enters a `while` loop that continues until the `right` index reaches the end of the prices array.
<br/>

Within the loop, it calculates the profit by subtracting the buying price (prices[left]) from the selling price (prices[right]).
<br/>

If the profit is greater than the current maximum profit (`max`), the `max` variable is updated.
<br/>

If the profit is negative, it means that the buying price is higher than the selling price. In this case, it updates the `left` variable to the current `right` index since we can't buy at a higher price than we sell.
<br/>

Finally, the `right` index is incremented by `1`, and the loop continues until it reaches the end of the prices array.
<br/>

The function returns the maximum profit that was calculated.
<br/>

In summary, the `maxProfit` function calculates the maximum profit that can be made by buying and selling a stock at different prices. It iterates through the prices array, keeps track of the lowest buying price and the maximum profit, and returns the maximum profit achieved.
<br/>
<br/>