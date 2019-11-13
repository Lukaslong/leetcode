## Valid brakets/有效的括号
### 问题描述：
给定一个只包括 '('，')'，'{'，'}'，'['，']' 的字符串，判断字符串是否有效。

有效字符串需满足：

    左括号必须用相同类型的右括号闭合。
    左括号必须以正确的顺序闭合。

注意空字符串可被认为是有效字符串。

##### 示例 1:

输入: "()"

输出: true

##### 示例 2:

输入: "()[]{}"

输出: true

##### 示例 3:

输入: "(]"

输出: false

##### 示例 4:

输入: "([)]"

输出: false

##### 示例 5:

输入: "{[]}"

输出: true

问题链接：https://leetcode-cn.com/problems/valid-parentheses

------------------
## 问题分析：
整体思路是从最外层不断往里深入，深入到字符串的最底层后，遇到一个右括号，则判断有没有最近的左括号与之匹配。

创建一个字典用以索引，然后创建一个空的列表stk，遍历输入字符串s的字符，如果是左括号，则压入列表stk，遇到右括号，则将stk中最后一个元素pop出来，利用字典判断两个括号是否匹配。不匹配则直接返回False，匹配则继续进行下一回合。

如果所有括号都是匹配的，那么stk列表最终仍然是空的，根据这一特性进行最终结果的判断。

这里需要注意的是，在创建字典时，右括号是作为key的，左括号作为value（遍历字典时，默认是遍历其key的，因此右括号作为key更方便）。

```
class Solution(object):
    def isValid(self, s):
        """
        :type s: str
        :rtype: bool
        """
        stk=[]
        dic={')':'(',']':'[','}':'{'}
        for ch in s:
            if ch in dic:
                top_element=stk.pop() if stk else '#'
                if top_element!=dic[ch]:
                    return False
            else:
                stk.append(ch)
        return not stk
```