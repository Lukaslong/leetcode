## minDepth/二叉树的最小深度

### 问题描述：

给定一个二叉树，找出其最小深度。

最小深度是从根节点到最近叶子节点的最短路径上的节点数量。

**说明:** 叶子节点是指没有子节点的节点。

**示例：**

给定二叉树[3, 9, 20, null, null, 15, 7]，

![leetcode_mindepth](/Users/zyl/Pictures/screenshot/leetcode_mindepth.png)

返回它的最小深度2。

问题链接：https://leetcode-cn.com/problems/minimum-depth-of-binary-tree/



### 问题分析：

本题看似简单，实则有陷阱，而陷阱就在于叶子结点的定义，叶子结点是没有任何子节点的节点，对于[1,2]二叉树，实际最小深度为2，而按照正常思路，很容易把结果算成1，如本人第一次写出的代码：

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def minDepth(self, root: TreeNode) -> int:
        if not root:
            return 0
        if not root.left or not root.right:
            return 1
        return 1+min(self.minDepth(root.left),self.minDepth(root.right))
```

这种解答的结果就是对于[1,2]二叉树，上面输出结果1，而实际答案应该是2，应该root节点并不是真正意义上的叶子结点。



主要问题出现在：**当一个子节点为空时，应返回非空子节点的深度**

所以正确解答应是：

```python
class Solution:
    def minDepth(self, root: TreeNode) -> int:
        if not root:
            return 0
        if not root.left and not root.right:
            return 1
        if not root.left or not root.right:
            return 1+self.minDepth(root.left)+self.minDepth(root.right)
        
        return 1+min(self.minDepth(root.left),self.minDepth(root.right))
```



