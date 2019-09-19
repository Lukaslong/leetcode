## addBinary/二进制求和
### 问题描述：
给定两个二进制字符串，返回他们的和（用二进制表示）。

输入为非空字符串且只包含数字 1 和 0。

##### 示例 1:

输入: a = "11", b = "1"

输出: "100"

##### 示例 2:

输入: a = "1010", b = "1011"

输出: "10101"

问题链接：https://leetcode-cn.com/problems/add-binary

-------
### 问题分析：
1.首先需要将两个字符串补齐到相同长度，最简单方法就是在短的字符串前面加上若干个'0'

2.从末尾开始遍历计算，对于是否需要进位，则可以通过对进位数p进行判断，p=1，则在前面加上'1'，p=0则直接返回ans

3.这里需要注意字符串加相加时的先后顺序不能调换，如不能简单a+=或ans+=，a+=x默认的相加顺序是a=a+x，结果和x+a是不一样的。
```
class Solution(object):
    def addBinary(self, a, b):
        """
        :type a: str
        :type b: str
        :rtype: str
        """
        ld=len(b)-len(a)
        ans,p='',0
        a='0'*ld+a
        b='0'*-ld+b
        for i,j in zip(a[::-1],b[::-1]):
            s=int(i)+int(j)+p
            ans=str(s%2)+ans
            p=s//2
        return '1'+ans if p else ans
```
（1）这里a='0'*ld+a , b='0'*-ld+b巧妙地避开了a和b长短的对比判断，可以计算下当ld为正和负时的'0'*-ld结果。

（2）zip(iterable1,iterable2,...)函数的作用是将可迭代对象打包成一个个元祖，然后返回由这些元组组成的列表。