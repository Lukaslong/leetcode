## isPalindrome/回文数判断
### 问题描述：
给定一个字符串，验证它是否是回文串，只考虑字母和数字字符，可以忽略字母的大小写。

说明：本题中，我们将空字符串定义为有效的回文串。

**示例 1:**
输入: "A man, a plan, a canal: Panama"
输出: true

**示例 2:**
输入: "race a car"
输出: false

问题链接：https://leetcode-cn.com/problems/valid-palindrome

----
### 问题分析：
输入字符串涉及到大小写字母、数字、空格以及其他符号等，但判断是否为回文数仅关注数字和字母，且不关注字母大小写。
因此可以首先将全部字符转化为小写，去除大小写字母的影响，然后逐一判断字符串中各字符是否为字母或数字，剔除字母&数字以为的字符。
当然以上“首先”和“然后”的内容也可颠倒，只是需要将大写字母也考虑进去。
```
class Solution:
    def isPalindrome(self, s: str) -> bool:
        s=s.lower()
        sn=[]
        for i in range(len(s)):
            if '0'<=s[i]<='9' or 'a'<=s[i]<='z':
                sn.append(s[i])
        return sn==sn[::-1]
```

当然还有抄近道，更快捷的方法，需要很强的Python函数积累，借助str.join()和filter()函数：
```
class Solution:
    def isPalindrome(self, s: str) -> bool:
    s = ''.join(filter(str.isalnum,s)).lower()
    return s==s[::-1]
```