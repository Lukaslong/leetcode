## maxNumberOfBalloons/最大气球数量
### 问题描述：
给定一个字符串 text，你需要使用 text 中的字母来拼凑尽可能多的单词 "balloon"（气球）。

字符串 text 中的每个字母最多只能被使用一次。请你返回最多可以拼凑出多少个单词 "balloon"。

##### 示例 1：
输入：text = "nlaebolko"

输出：1

##### 示例 2：
输入：text = "loonbalxballpoon"

输出：2

##### 示例 3：
输入：text = "leetcode"

输出：0
 
##### 提示：
1 <= text.length <= 10^4

text 全部由小写英文字母组成

问题链接：https://leetcode-cn.com/problems/maximum-number-of-balloons

### 问题分析：
根据题意，这里不考虑字母出现的先后顺序，只需统计字母出现的频次即可。

Python的字典和list派上用场，字典用于存储balloon各字母对应的数字，而list用于统计各字母出现的频次。

最终根据各字母出现的频次，分别除以balloon中各字母的频次（地板除），取最小值即可。

```
class Solution(object):
    def maxNumberOfBalloons(self, text):
        """
        :type text: str
        :rtype: int
        """
        dic={'b':0,'a':1,'l':2,'o':3,'n':4}
        l=[0]*5
        for i,letter in enumerate(text):
            if dic.get(letter,-1)!=-1:
                l[dic.get(letter)]+=1
        print(l[0],l[1],l[2]//2,l[3]//2,l[4])
        return min(l[0],l[1],l[2]//2,l[3]//2,l[4])
```
需要注意的是，在进行text中字母是否在dic中的判断时，这里用的是if dic.get(letter,-1)!=-1，而不是简单的if dic.get(letter)，否则'b'对应的value永远都无法被dic.get('b')=0)。