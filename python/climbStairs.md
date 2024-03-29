## climbStairs/爬楼梯
### 问题描述：
假设你正在爬楼梯。需要 n 阶你才能到达楼顶。

每次你可以爬 1 或 2 个台阶。你有多少种不同的方法可以爬到楼顶呢？

注意：给定 n 是一个正整数。
##### 示例 1：
输入： 2

输出： 2

解释： 有两种方法可以爬到楼顶。

1 阶 + 1 阶

2 阶

##### 示例 2：
输入： 3

输出： 3

解释： 有三种方法可以爬到楼顶。

1 阶 + 1 阶 + 1 阶

1 阶 + 2 阶

2 阶 + 1 阶

问题链接：https://leetcode-cn.com/problems/climbing-stairs

--------
### 问题分析：
首先是找规律，不难发现当n=1,2,3,4,5,6,...时，结果分别为1,2,3,5,8,13,...这可不就是斐波那契数列嘛，ans[n]=ans[n-1]+ans[n-2],可以通过递归的思想进行解答：

```
class Solution(object):
    def climbStairs(self, n):
        """
        :type n: int
        :rtype: int
        """
        ans=[]
        ans.append(1)
        ans.append(2)
        for i in range(2,n):
            tmp=ans[i-1]+ans[i-2]
            ans.append(tmp)
        return ans[n-1]
```