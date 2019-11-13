## Two Sum/两数之和
### 问题描述：
给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。

你可以假设每种输入只会对应一个答案。但是，你不能重复利用这个数组中同样的元素。

##### 示例:

给定 nums = [2, 7, 11, 15], target = 9

因为 nums[0] + nums[1] = 2 + 7 = 9
所以返回 [0, 1]

----------------
### 问题分析：
##### 1. 直接遍历
最简单粗暴的方法是执行两次遍历，由于元素不能重复使用，因此第一层遍历是从第1个元素到len(nums)-1，第二层遍历是从第2个元素到len(nums)。
每次判断两数之和是否等于targets，满足条件则返回该两个元素的序号，即完成题解。
最坏的情况是循环(n-1)+(n-2)+...+1=n(n-1)/2，即时间复杂度为O(n²)
```
class Solution(object):
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        for i in range(len(nums)-1):
            for j in range(i+1,len(nums)):
                if nums[i]+nums[j]==target:
                    return [i,j]
```
##### 2. 创建哈希表，通过dictionary实现
借鉴哈希表的方法，通过Python中字典将nums数组中的元素和下标映射到字典中，再遍历nums中元素时，只需每次判断字典中是否有匹配target-nums[i]的value。
因此本方法只需一次遍历，时间复杂度O(n)。
```
class Solution(object):
    def twoSum(self, nums, target):
        """
        :type nums: List[int]
        :type target: int
        :rtype: List[int]
        """
        dic={}
        for ind,num in enumerate(nums):
            dic[num]=ind
        for i in range(len(nums)):
            j=dic.get(target-nums[i])
            if j and j!=i:
                return [i,j]
```