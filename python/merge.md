## merge/合并两个有序数组
### 问题描述：
给定两个有序整数数组 nums1 和 nums2，将 nums2 合并到 nums1 中，使得 num1 成为一个有序数组。

说明:

初始化 nums1 和 nums2 的元素数量分别为 m 和 n。

可以假设 nums1 有足够的空间（空间大小大于或等于 m + n）来保存 nums2 中的元素。

##### 示例:

输入:
nums1 = [1,2,3,0,0,0], m = 3

nums2 = [2,5,6], n = 3

输出: [1,2,2,3,5,6]

问题链接：https://leetcode-cn.com/problems/merge-sorted-array

-------------
### 问题分析
之前有过一道及其相似的题目，即“合并两个有序链表”。

两题解法也是共通的，区别是 1. 本题要求最终结果存储在其中一个数组中nums1，不能开辟新的数组（这样的情况就太简单了）； 2. 比较完成后的操作，链表比较简单，直接把没用完的链表剩余部分附上新链表后面即可，数组则不然。

由于nums1数组后面有空白部分，因此从这部分入手，不会覆盖输入的信元素息，即从后端入手，从大到小排序。对于剩余的部分，只需对nums2进行判断即可，如果是nums1数组没用完，不用理会；如果是nums2数组没用完，则附在前面即可。
```
class Solution(object):
    def merge(self, nums1, m, nums2, n):
        """
        :type nums1: List[int]
        :type m: int
        :type nums2: List[int]
        :type n: int
        :rtype: None Do not return anything, modify nums1 in-place instead.
        """
        while m>=1 and n>=1:
            if nums1[m-1]>=nums2[n-1]:
                nums1[m+n-1]=nums1[m-1]
                m-=1
            else:
                nums1[m+n-1]=nums2[n-1]
                n-=1
        if n:
            nums1[0:n]=nums2[0:n]
        return nums1
```