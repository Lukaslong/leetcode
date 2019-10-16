## isBalanced/平衡二叉树判断

### 问题描述：

给定一个二叉树，判断它是否为高度平衡的二叉树。

高度平衡二叉树定义为：

>一个二叉树每个节点的左右两个子树的高度差的绝对值不超过1.

**示例1：**

给定二叉树[3, 9, 20, null, null, 15, 7]

![image-20191016144544955](/Users/zyl/Library/Application Support/typora-user-images/image-20191016144544955.png)

返回true。



**示例2:**

给定二叉树[1, 2, 2, 3, 3, null, null, 4, 4]

![image-20191016144716940](/Users/zyl/Library/Application Support/typora-user-images/image-20191016144716940.png)

返回false。



问题链接：https://leetcode-cn.com/problems/balanced-binary-tree/



### 问题分析：

两种方法，第一种比较直观，即从上至下，由于之前的题目中已经练习过求解二叉树最大深度的方法了，因此这里直接通过构造深度函数，利用递归即可完成：

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def isBalanced(self, root: TreeNode) -> bool:
        if not root:
            return True
        return abs(self.maxDepth(root.left)-self.maxDepth(root.right))<=1 and self.isBalanced(root.left) and self.isBalanced(root.right)
        return 
    def maxDepth(self,root:TreeNode)->int:
        if not root:
            return 0
        if not root.left and not root.right:
            return 1
        return 1+max(self.maxDepth(root.left),self.maxDepth(root.right))
```



第二种方法：由下而上

提前截断，一旦发现左右子树的高度差大于1，即返回结果。

```python
class Solution:
    def isBalanced(self, root: TreeNode) -> bool:
        return self.depth(root)!=-1
    def depth(self,root:TreeNode)->int:
        if not root:
            return 0
        left=self.depth(root.left)
        if left==-1:
            return -1
        right=self.depth(root.right)
        if right==-1:
            return -1
        return 1+max(left,right) if abs(left-right)<2 else -1
```



