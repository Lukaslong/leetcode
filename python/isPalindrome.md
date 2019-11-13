## isPalindrome/回文数
### 问题描述：
判断一个整数是否是回文数。回文数是指正序（从左向右）和倒序（从右向左）读都是一样的整数。

#### 示例 1:

输入: 121

输出: true

#### 示例 2:

输入: -121

输出: false

解释: 从左向右读, 为 -121 。 从右向左读, 为 121- 。因此它不是一个回文数。

#### 示例 3:

输入: 10

输出: false

解释: 从右向左读, 为 01 。因此它不是一个回文数。

---------------------------
### 问题分析：
##### 1.list切片法
显然，将数字转换为字符串，然后利用list切片操作即可完成反转，然后判断和原数字对应的字符串是否相等即可，仅需一行代码：
```
class Solution(object):
    def isPalindrome(self, x):
        """
        :type x: int
        :rtype: bool
        """
        return True if str(x)==str(x)[::-1] else False
```
##### 2.直接计算反转的结果
但是题目并不想让我们这么简单糊弄过去。如果不将整数转化为字符串呢？那就硬算啊：
```
class Solution(object):
    def isPalindrome(self, x):
        """
        :type x: int
        :rtype: bool
        """
        if x<0:
            return False
        x1,ans=x,0
        while x1>0:
            ans=ans*10+x1%10
            x1=x1//10
        return x==ans
```
解题思路：如果输入为负数，那结果自然是False,因此首先进行了正负号的判断。
然后计算正整数反转后的结果，即不断取余、地板除更新x和结果。
最后判断ans和x是否相等。

