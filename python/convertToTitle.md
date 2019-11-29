## convertToTitle/Excel表列名称转换
### 问题描述：
给定一个正整数，返回它在 Excel 表中相对应的列名称。

例如，

    1 -> A
    2 -> B
    3 -> C
    ...
    26 -> Z
    27 -> AA
    28 -> AB 
    ...

**示例 1:**

输入: 1

输出: "A"

**示例 2:**

输入: 28

输出: "AB"

**示例 3:**

输入: 701

输出: "ZY"

问题链接：https://leetcode-cn.com/problems/excel-sheet-column-title

### 问题分析：
其实很像十进制转到十六进制的问题，只不过这里数字需要统一转换为A-Z的字母。

另外就是需要借助chr函数以及ASCII码（'A'对应65）。

```
class Solution:
    def convertToTitle(self, n: int) -> str:
        d={}
        for i in range(26):
            d[i]=chr(65+i)
        s=''
        while n:
            n-=1
            s=d[n%26]+s
            n=n//26
        return s     
```

其实，根本不用创建字典这一中间过程，直接将每次取模的结果转换到字母就可以了。

```
class Solution:
    def convertToTitle(self, n: int) -> str:
        s=''
        while n:
            n-=1
            s=chr(65+n%26)+s
            n=n//26
        return s  
```