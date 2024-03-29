## strStr/实现strStr()
### 问题描述：
给定一个 haystack 字符串和一个 needle 字符串，在 haystack 字符串中找出 needle 字符串出现的第一个位置 (从0开始)。如果不存在，则返回  -1。

##### 示例 1:
输入: haystack = "hello", needle = "ll"

输出: 2

##### 示例 2:
输入: haystack = "aaaaa", needle = "bba"

输出: -1

##### 说明:
当 needle 是空字符串时，我们应当返回什么值呢？这是一个在面试中很好的问题。

对于本题而言，当 needle 是空字符串时我们应当返回 0 。这与C语言的 strstr() 以及 Java的 indexOf() 定义相符。

问题链接：https://leetcode-cn.com/problems/implement-strstr

----------
### 问题分析：
利用list的切片特性，从0遍历到len(haystack)-len(needle)，判断haystack[i:i+nl]和needle是否相等。

这里使用了while循环，而非for循环是因为最后用i判断循环终止的条件，如果是因为i>len(haystack)-len(needle)，则意味着haystack不包含needle，返回-1.
```
class Solution(object):
    def strStr(self, haystack, needle):
        """
        :type haystack: str
        :type needle: str
        :rtype: int
        """
        if not needle:
            return 0
        hl=len(haystack)
        nl=len(needle)
        i=0
        while i<=hl-nl:
            if haystack[i:i+nl]==needle:
                return i
            i+=1
        if i>hl-nl:
            return -1
```