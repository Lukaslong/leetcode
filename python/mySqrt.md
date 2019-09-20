## mySqrt/平方根
### 问题描述：
手动实现int sqrt(int x) 函数：计算并返回 x 的平方根，其中 x 是非负整数。

由于返回类型是整数，结果只保留整数的部分，小数部分将被舍去。
##### 示例 1：
输入：4

输出：2

##### 示例 2：
输入：8

输出：2

------------
### 问题分析：
题目看似简单，直观做法是直接遍历从0遍历到x，或遍历到x/2，首先不说时间复杂度O(n)，当输入数较大时也容易报内存的错。

比较进阶的方法是二分法，时间复杂度O(logn)，但需注意：
1.因为输入可能为0，所以左侧从0开始；

2.正常右侧可以从x/2开始，但为了照顾x=1的情况，右边界设置为x//2+1

3.由于最后结果是向下取整，因此每次begin更新要注意，应是mid，而不用+1，否则最后需要加判断

4.mid取右中位数，而非左中位数，否则会陷入死循环

```
class Solution(object):
    def mySqrt(self, x):
        """
        :type x: int
        :rtype: int
        """
        begin,end=0,x//2+1
        while end>begin:
            mid=(end+begin+1)//2
            if mid**2==x:
                return mid
            elif mid**2<x:
                begin=mid
            else:
                end=mid-1
        return begin
```