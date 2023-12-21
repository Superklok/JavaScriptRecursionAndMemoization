# JavaScript Best Time to Buy and Sell Stock

## Challenge:

You are given an array `prices` where `prices[i]` is the price of a given stock on the `iᵗʰ` day.

You want to maximize your profit by choosing a single day to buy one stock and choosing a different day in the future to sell that stock.

Return the maximum profit you can achieve from this transaction. If you cannot achieve any profit, return `0`.

### 1<sup>st</sup> Example:

`Input: prices = [7,1,5,3,6,4]`
<br/>
`Output: 5`
<br/>
`Explanation: Buy on day 2 (price = 1) and sell on day 5 (price = 6), profit = 6-1 = 5.`
<br/>
`Note that buying on day 2 and selling on day 1 is not allowed because you must buy before you sell.`

### 2<sup>nd</sup> Example:

`Input: prices = [7,6,4,3,1]`
<br/>
`Output: 0`
<br/>
`Explanation: In this case, no transactions are done and the max profit = 0.`

### Constraints:

`1 <= prices.length <= 10⁵`
<br/>
`0 <= prices[i] <= 10⁴`

## Solution:

`const maxProfit = (prices) => {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`let max   = 0,`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`left  = 0,`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`right = 1;`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`while(right < prices.length) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`const profit = prices[right] - prices[left];`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`if(profit > max) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`max = profit;`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`if(profit < 0) {`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`left = right;`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`right += 1;`
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`}`
<br/>
<br/>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;`return max;`
<br/>
`};`
<br/>
<br/>

## Explanation:

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