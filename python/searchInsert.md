## searchInsert/搜索插入位置
### 问题描述：
给定一个排序数组和一个目标值，在数组中找到目标值，并返回其索引。如果目标值不存在于数组中，返回它将会被按顺序插入的位置。

可以假设数组中无重复元素。

##### 示例 1:

输入: [1,3,5,6], 5

输出: 2

##### 示例 2:

输入: [1,3,5,6], 2

输出: 1

##### 示例 3:

输入: [1,3,5,6], 7

输出: 4

##### 示例 4:

输入: [1,3,5,6], 0

输出: 0

问题链接：https://leetcode-cn.com/problems/search-insert-position

--------
### 问题分析：
典型的排序问题啦，当然采用二分法，时间复杂度比较低。

要注意的是最后返回左值left，而不是右边right；每次mid赋值为left+1或rught-1，如果没有加1或减1，很容易进入死循环。如left=3，right=4，如果没有加1减1，当nums[mid]小于target时，mid将一直等于left，陷入死循环。

```
class Solution(object):
    def searchInsert(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: int
        """
        '''
        for i in range(len(nums)):
            if target<=nums[i]:
                return i
            if i==(len(nums)-1):
                return len(nums)
            elif target<nums[i+1]:
                return i+1
        '''
        left,right=0,len(nums)-1
        while left<=right:
            mid=int(left+(right-left)/2)
            if nums[mid]==target:
                return mid
            elif nums[mid]>target:
                right=mid-1
            else:
                left=mid+1
        return left
```