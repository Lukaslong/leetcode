## twoSum2/两数之和II
### 问题描述：

给定一个已按照升序排列 的有序数组，找到两个数使得它们相加之和等于目标数。

函数应该返回这两个下标值 index1 和 index2，其中 index1 必须小于 index2。

**说明:**

返回的下标值（index1 和 index2）不是从零开始的。

你可以假设每个输入只对应唯一的答案，而且你不可以重复使用相同的元素。

**示例:**

输入: numbers = [2, 7, 11, 15], target = 9

输出: [1,2]

解释: 2 与 7 之和等于目标数 9 。因此 index1 = 1, index2 = 2 。

问题链接：https://leetcode-cn.com/problems/two-sum-ii-input-array-is-sorted

----
### 问题分析：
既然是已经排好序的数组，那么可以通过首尾双指针来实现。

依次判断头尾指针的元素之和与target的关系，和大于target，则尾指针向前进一位；

相反，和小于target则头指针向后进一位；

直到和值等于target，或头尾指针相遇，则结束循环，返回。

```
class Solution:
    def twoSum(self, numbers: List[int], target: int) -> List[int]:
        if not numbers:
            return []
        index1,index2=1,len(numbers)
        while index2>index1:
            if numbers[index1-1]+numbers[index2-1]==target:
                return [index1,index2]
            if numbers[index1-1]+numbers[index2-1]>target:
                index2-=1
            if numbers[index1-1]+numbers[index2-1]<target:
                index1+=1
        return []
```