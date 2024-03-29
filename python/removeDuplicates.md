## Remove Duplicates/移除有序数组中重复项
### 问题描述：
给定一个排序数组，你需要在原地删除重复出现的元素，使得每个元素只出现一次，返回移除后数组的新长度。

不要使用额外的数组空间，你必须在原地修改输入数组并在使用 O(1) 额外空间的条件下完成。

不需要考虑数组中超出新长度后面的元素。
##### 示例 1:

给定数组 nums = [1,1,2], 

函数应该返回新的长度 2, 并且原数组 nums 的前两个元素被修改为 1, 2。 
##### 示例 2:

给定 nums = [0,0,1,1,1,2,2,3,3,4],

函数应该返回新的长度 5, 并且原数组 nums 的前五个元素被修改为 0, 1, 2, 3, 4。

问题链接：https://leetcode-cn.com/problems/remove-duplicates-from-sorted-array

-----------------------------
### 问题分析：
这里关键信息是不允许创建新的数组，只能在原来数组基础上进行修改，但无需考虑超出新长度以外的元素。

可以采用补位的方式，发现重复元素后，用后面不重复的元素覆盖，由于重复元素可能不止一个，因此需要两个指针，一个指向当前位置，一个指向后面不重复的新元素。

```
class Solution(object):
    def removeDuplicates(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        if nums==[]:
            return 0
        i,j=0,1
        while j<len(nums):
            if nums[i]!=nums[j]:
                i+=1
                nums[i]=nums[j]
            j+=1
        return i+1        
```
需要提到的是，在判断nums[i]和nums[j]的关系时，采用的是当两者不相等时，分别向前进一位。这样比判断两者相等后进行动作简单些。