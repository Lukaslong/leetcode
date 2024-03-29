## maxProfit/买卖股票的最大利润
### 问题描述：
给定一个数组，它的第 i 个元素是一支给定股票第 i 天的价格。

如果你最多只允许完成一笔交易（即买入和卖出一支股票），设计一个算法来计算你所能获取的最大利润。

注意你不能在买入股票前卖出股票。

**示例 1:**
输入: [7,1,5,3,6,4]
输出: 5
解释: 在第 2 天（股票价格 = 1）的时候买入，在第 5 天（股票价格 = 6）的时候卖出，最大利润 = 6-1 = 5 。
     注意利润不能是 7-1 = 6, 因为卖出价格需要大于买入价格。

**示例 2:**
输入: [7,6,4,3,1]
输出: 0
解释: 在这种情况下, 没有交易完成, 所以最大利润为 0。

问题链接：https://leetcode-cn.com/problems/best-time-to-buy-and-sell-stock

------
### 问题分析：
典型的动态规划问题。
（1）将今天的价格和之前的最低价对比，获取买入最低成本
（2）将今天的利润和之前的最大利润对比，获取最大利润
（3）今天的利润为当前价格-当前最低价
```
class Solution:
    def maxProfit(self, prices: List[int]) -> int:
        if not prices:
            return 0
        min_p,max_p=prices[0],0
        for i in range(len(prices)):
            min_p=min(min_p,prices[i])
            max_p=max(max_p,prices[i]-min_p)
        return max_p
```