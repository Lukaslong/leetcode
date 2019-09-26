## isSymmetric/对称二叉树判断
### 问题描述：
给定一个二叉树，检查它是否是镜像对称的。

例如，二叉树 [1,2,2,3,4,4,3] 是对称的：
![avatar](/home/zyl/Pictures/对称二叉树1.png)

但是下面这个 [1,2,2,null,3,null,3] 则不是镜像对称的:
![avatar](/home/zyl/Pictures/对称二叉树2.png)

问题链接：https://leetcode-cn.com/problems/symmetric-tree

-----------
### 问题分析：
和之前判断两个二叉树是否相同的题目类似，可以通过递归来实现。但这里不是直接在原函数上实现的，而是另写了一个判断是否为镜像的递归函数。
```
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def isSymmetric(self, root):
        """
        :type root: TreeNode
        :rtype: bool
        """
        if not root:
            return True
        return self.isMirror(root.left,root.right)
        
    def isMirror(self,root1,root2):
        if not root1 and not root2:
            return True
        if not root1 or not root2:
            return False
        if root1.val!=root2.val:
            return False
        return self.isMirror(root1.left,root2.right) and self.isMirror(root1.right,root2.left)
```

