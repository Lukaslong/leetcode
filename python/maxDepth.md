## maxDepth/二叉树的最大深度
### 问题描述：
给定一个二叉树，找出其最大深度。

二叉树的深度为根节点到最远叶子节点的最长路径上的节点数。

说明: 叶子节点是指没有子节点的节点。

##### 示例：
给定二叉树 [3,9,20,null,null,15,7]：
![avatar](/home/zyl/Pictures/二叉树最大深度.png)

问题链接：https://leetcode-cn.com/problems/maximum-depth-of-binary-tree

-----------
### 问题分析：
二叉树问题最适合的还是递归：
```
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def maxDepth(self, root):
        """
        :type root: TreeNode
        :rtype: int
        """
        if not root:
            return 0
        if not root.left and not root.right:
            return 1
        return 1+max(self.maxDepth(root.left),self.maxDepth(root.right))
```