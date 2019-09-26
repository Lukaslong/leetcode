## levelOrderBottom/二叉树的层次遍历
### 问题详情：
给定一个二叉树，返回其节点值自底向上的层次遍历。（即按从叶子节点所在层到根节点所在的层，逐层从左向右遍历）

例如：

给定二叉树 [3,9,20,null,null,15,7],
![avatar](/home/zyl/Pictures/遍历二叉树1.png)

返回其自底向上的层次遍历为：

![avatar](/home/zyl/Pictures/遍历二叉树2.png)

问题链接：https://leetcode-cn.com/problems/binary-tree-level-order-traversal-ii

---------------
### 问题分析：
本次二叉树问题因为输出格式，无法再用递归解决，否则输出结果则为层层嵌套。

采用层层遍历的方式：
```
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def levelOrderBottom(self, root):
        """
        :type root: TreeNode
        :rtype: List[List[int]]
        """
        rl=[]
        cur=[root]
        while cur:
            tmpl=[]
            next_level=[]
            for node in cur:
                if node:
                    tmpl.append(node.val)
                    next_level.extend([root.left,root.right])
            if tmpl:
                rl.insert(0,tmpl)
            curl=next_level
        return rl
```
这里使用了list的三种插入方式，append，extend，insert，具体区别在解答里有所体现。