## Two Sum/两数之和
### 问题描述：
给定一个整数数组 nums 和一个目标值 target，请你在该数组中找出和为目标值的那 两个 整数，并返回他们的数组下标。

你可以假设每种输入只会对应一个答案。但是，你不能重复利用这个数组中同样的元素。

#### 示例:

给定 nums = [2, 7, 11, 15], target = 9

因为 nums[0] + nums[1] = 2 + 7 = 9
所以返回 [0, 1]

### 问题分析：
最直接的方法是执行两次遍历，由于元素不能重复使用，因此第一层遍历是从第1个元素到len(nums)-1，第二层遍历是从第2个元素到len(nums)。
每次遍历后判断两数之和是否等于targets，满足条件则返回该两个元素的序号，即完成题解。

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
