## plusOne/加一
### 问题描述：
给定一个由整数组成的非空数组所表示的非负整数，在该数的基础上加一。

最高位数字存放在数组的首位， 数组中每个元素只存储单个数字。

可以假设除了整数 0 之外，这个整数不会以零开头。

##### 示例 1:
输入: [1,2,3]

输出: [1,2,4]

解释: 输入数组表示数字 123。

##### 示例 2:
输入: [4,3,2,1]

输出: [4,3,2,2]

解释: 输入数组表示数字 4321。

问题链接：https://leetcode-cn.com/problems/plus-one

---------
### 问题分析：
问题相当于手动实现最基础的加法操作，涉及到进位操作，但需要注意的是结果的位数可能会多出一位，因此数组的长度也会增大。

```
class Solution(object):
    def plusOne(self, digits):
        """
        :type digits: List[int]
        :rtype: List[int]
        """
        digits[-1]+=1
        i=len(digits)-1
        while i>0:
            digits[i-1]+=digits[i]//10
            digits[i]%=10
            i-=1
        if digits[0]==10:
            digits[0]=1
            digits.append(0)
        return digits
```