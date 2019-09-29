## sortedArrayToBST/有序数组转换为二叉树
### 问题描述：
将一个按照升序排列的有序数组，转换为一棵高度平衡二叉搜索树。

本题中，一个高度平衡二叉树是指一个二叉树每个节点 的左右两个子树的高度差的绝对值不超过 1。

##### 示例:

给定有序数组: [-10,-3,0,5,9],

一个可能的答案是：[0,-3,9,-10,null,5]，它可以表示下面这个高度平衡二叉搜索树：

![avatar](/home/zyl/Pictures/zhuanhuanerchashu.png)

链接：https://leetcode-cn.com/problems/convert-sorted-array-to-binary-search-tree

-------
### 问题分析：
题目要求高度平衡，其实这是一个比较容易满足的条件，只要不一味地在一侧建树即可。

本人首先想到的方法是通过二叉树节点数和层数的关系，获取二叉树的深度，然后从第一层一点点地建立二叉树，但进行到第三层的时候显然就无法进行下去了。

看了解答中大神们的结果，受到很大启发，本题这种深度未知的二叉树问题，显然还是通过递归来实现呀。结合二分法，可以让递归得以实现，同时满足题目中关于高度平衡的要求。

通过编写函数buildTree(self,nums,begin,end)实现：
```
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def sortedArrayToBST(self, nums):
        """
        :type nums: List[int]
        :rtype: TreeNode
        """
        begin=0
        end=len(nums)-1
        return self.buildTree(nums,begin,end)
    
    def buildTree(self,nums,begin,end):
        if begin>end:
            return None
        mid=(begin+end)>>1
        node=TreeNode(nums[mid])
        node.left=self.buildTree(nums,begin,mid-1)
        node.right=self.buildTree(nums,mid+1,end)
        return node
```
其实本题示例的结果中也相当于给了提示，即使用二分法。