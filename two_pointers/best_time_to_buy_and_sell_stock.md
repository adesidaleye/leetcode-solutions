# Best Time to Buy and Sell Stock

[Problem Link](https://leetcode.com/problems/best-time-to-buy-and-sell-stock)

## Goal
Today I tackled the classic "Best Time to Buy and Sell Stock". The task is to find the largest profit from a single buy/sell pair in an array of daily prices. It’s a quick win that tests greedy thinking and edge‑case handling.

## Approach
I started with the brute force idea of checking every pair, but that blew up to O(N^2). Then I remembered the greedy pattern: keep a running minimum price and compute profit against each new price. The key insight was that the best sell day for a given buy is always the maximum price after that buy, so I only need to update the min when I see a lower one. I used two pointers—left for the buy index and right for the sell index—moving right across the array. Whenever the current price is lower than the left, I shift the buy pointer; otherwise, I compute profit and update the max. That single pass is all I need.

## Code
```java
class Solution {
    public int maxProfit(int[] prices) {
        int maxProfit = 0;
        int left = 0;
        int right = 1;

        while (right < prices.length) {
            if (prices[right] > prices[left]) {
                int profit = prices[right] - prices[left];
                maxProfit = Math.max(maxProfit, profit);
            } else {
                left = right;
            }

            right++;
        }

        return maxProfit;
    }
}
```

## Complexities
- Time complexity: O(N)
- Space complexity: O(1)

## Screenshot
![screenshot](https://res.cloudinary.com/dyyyjtqir/image/upload/v1790108871/l9lojchrlu4uycm1sa7p.png)
