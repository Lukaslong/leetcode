## Longest Common Prefix/最长公共前缀
### 问题描述
编写一个函数来查找字符串数组中的最长公共前缀。

如果不存在公共前缀，返回空字符串 ""。

##### 示例 1:

输入: ["flower","flow","flight"]

输出: "fl"

##### 示例 2:

输入: ["dog","racecar","car"]

输出: ""

解释: 输入不存在公共前缀。

##### 说明:

所有输入只包含小写字母 a-z 。

问题链接：https://leetcode-cn.com/problems/longest-common-prefix

----------
### 问题分析：
由于最长公共前缀的长度事先是未知的，因此需要从长到短的方向缩小，但最长不会超过字符串数组strs中最短的那个，因此公共前缀初始化为第一个字符串的前minl个字符（minl为字符串数组中最短的字符串长度）。
最外层的遍历依旧是数组元素的遍历，里面一层遍历则是公共前缀从长到短的不断缩小，直到被当前字符串真包含。
```
class Solution(object):
    def longestCommonPrefix(self, strs):
        """
        :type strs: List[str]
        :rtype: str
        """
        if not strs:
            return ''
        minl=min(len(strs[i]) for i in range(len(strs)))
        rstr=strs[0][:minl]
        for i in range(len(strs)):
            while strs[i][:len(rstr)]!=rstr:
                rstr=rstr[:len(rstr)-1]
                if not rstr:
                    return ''
        return rstr
```
