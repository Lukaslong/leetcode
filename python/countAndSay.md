## countAndSay/报数
### 问题描述：
报数序列是一个整数序列，按照其中的整数的顺序进行报数，得到下一个数。其前五项如下：

1.     1
2.     11
3.     21
4.     1211
5.     111221

1 被读作  "one 1"  ("一个一") , 即 11。

11 被读作 "two 1s" ("两个一"）, 即 21。

21 被读作 "one 2",  "one 1" （"一个二" ,  "一个一") , 即 1211。

给定一个正整数 n（1 ≤ n ≤ 30），输出报数序列的第 n 项。

注意：整数顺序将表示为一个字符串。
 
##### 示例 1:
输入: 1

输出: "1"

##### 示例 2:

输入: 4

输出: "1211"

问题链接：https://leetcode-cn.com/problems/count-and-say

----------
### 问题分析：
1. 先设置上一人为'1'
2. 开始外循环
3. 每次外循环先置下一人为空字符串，置待处理的字符num为上一人的第一位，置记录出现的次数为1
4. 开始内循环，遍历上一人的数，如果数是和num一致，则count增加。
5. 若不一致，则将count和num一同添加到next_person报的数中，同时更新num和count
6. 更新next_person的最后两个数为上一个人最后一个字符以及其出现次数！

解题链接：https://leetcode-cn.com/problems/count-and-say/solution/ji-su-jie-bu-di-gui-zhi-ji-lu-qian-hou-liang-ren-p/
```
class Solution(object):
    def countAndSay(self, n):
        """
        :type n: int
        :rtype: str
        """
        pre_num='1'
        for i in range(1,n):
            next_num,num,count='',pre_num[0],1
            for k in range(1,len(pre_num)):
                if pre_num[k]==num:
                    count+=1
                else:
                    next_num+=str(count)+num
                    num=pre_num[k]
                    count=1
            next_num+=str(count)+num
            pre_num=next_num
        return pre_num
```