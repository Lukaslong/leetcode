## Integer Reverse/整数反转
### 问题描述：
给出一个 32 位的有符号整数，你需要将这个整数中每位上的数字进行反转。

另外，假设环境只能存储得下 32 位的有符号整数，则其数值范围为[−2^31,  2^31 − 1]。请根据这个假设，如果反转后整数溢出那么就返回 0。

##### 示例1：

输入: 123
输出: 321

##### 示例 2:

输入: -123
输出: -321

##### 示例 3:

输入: 120
输出: 21

-----------------
### 问题分析
提到整数或者字符串反转，首先想到的应该是列表list的切片操作，利用列表切片可以直接完成字符串的反转。

但这里需要注意的是整数可以为负数，因此首先需要判断输入的正负。另外还有范围的限制，反转后的结果应落在[−2^31,  2^31 − 1]，超出范围则输出0。

```
class Solution(object):
    def reverse(self, x):
        """
        :type x: int
        :rtype: int
        """
        INT_MAX=2**31
        x_str=str(x)
        if x>=0:
            ans=int(x_str[::-1])
        else:
            ans=-int(x_str[::-1][:-1])
        return ans if ans<INT_MAX and ans>-INT_MAX else 0
```