## isSameTree/相同的二叉树判断
### 问题描述：
给定两个二叉树，编写一个函数来检验它们是否相同。

如果两个树在结构上相同，并且节点具有相同的值，则认为它们是相同的。

##### 示例 1:
![avatar](/home/zyl/Pictures/示例1.png)

##### 示例 2:
![avatar](/home/zyl/Pictures/示例2.png)

##### 示例 3:
![avatar](/home/zyl/Pictures/示例3.png)

问题链接：https://leetcode-cn.com/problems/same-tree

---------------
### 问题分析：
这类问题最适合的解决方案是递归，首先列出能判断结果的情况，即：1. p和q都为空，则为True；  2. 其中一个为空，False； 3. 一旦出现p.val!=q.val, False； 4. 都不符合，则进行下一层两个节点的判断。
```
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def isSameTree(self, p, q):
        """
        :type p: TreeNode
        :type q: TreeNode
        :rtype: bool
        """
        if not p and not q:
            return True
        if not p or not q:
            return False
        if p.val!=q.val:
            return False
        return self.isSameTree(p.left,q.left) and self.isSameTree(p.right,q.right)
```
