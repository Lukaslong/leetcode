## Pascals-Triangle/杨辉三角
### 问题描述：
给定一个非负整数 numRows，生成杨辉三角的前 numRows 行。

![avatar](https://upload.wikimedia.org/wikipedia/commons/0/0d/PascalTriangleAnimated2.gif)

在杨辉三角中，每个数是它左上方和右上方的数的和。

##### 示例：
输入: 5
输出:
[
&ensp;&ensp;&ensp;&ensp;&ensp;[1],
&ensp;&ensp;&ensp;&ensp;[1,1],
&ensp;&ensp;&ensp;[1,2,1],
&ensp;&ensp;[1,3,3,1],
&ensp;[1,4,6,4,1]
]

问题来源：https://leetcode-cn.com/problems/pascals-triangle/

------

### 问题分析：
通过观察可以发现规律，第n行共有n个元素，因此方法是直接通过两层循环：

```
class Solution:
    def generate(self, numRows: int) -> List[List[int]]:
        if numRows==0:
            return []
        ans=[[1]]
        if numRows==1:
            return ans
        for i in range(1,numRows):
            pre=ans[i-1]
            tmp=[]
            tmp.append(pre[0])
            for j in range(1,i):
                tmp.append(pre[j-1]+pre[j])
            tmp.append(pre[-1])
            ans.append(tmp)
        return ans    
```
稍需注意的是，题目指出输入是非负数，因此输入可能为0，此时返回空list即可。
