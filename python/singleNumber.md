## singleNumber/只出现一次的数字
### 问题描述：
给定一个非空整数数组，除了某个元素只出现一次以外，其余每个元素均出现两次。找出那个只出现了一次的元素。

说明：

你的算法应该具有线性时间复杂度。 你可以不使用额外空间来实现吗？

**示例 1:**
输入: [2,2,1]
输出: 1

**示例 2:**
输入: [4,1,2,1,2]
输出: 4

问题链接：https://leetcode-cn.com/problems/single-number

------
### 问题分析：
1.直接遍历
创建新的列表，遍历nums中的元素：
如果新列表中不存在该元素，则添加至新列表；
如果新列表存在该元素，说明该元素出现两次，从新列表中将之前添加的该元素剔除；
最后新列表中只剩下那个只出现一次的元素，pop出来即可。
```
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        tmp=[]
        for i in nums:
            if i not in tmp:
                tmp.append(i)
            else:
                tmp.remove(i)
        return tmp.pop()
```
虽然也能解出本题，但与本题的初衷不太相符，时间复杂度和空间复杂度高，分别为O(n²)和O(n)。

**2.位操作**
查看问题解答发现一种更快捷的解法，即使用二进制位的异或运算XOR。
(1) XOR满足交换律和结合律
　a⊕b⊕a=(a⊕a)⊕b=0⊕b=b
(2)对相同的二进制位做 XOR 运算，返回的结果是 0
　a⊕a=0
(3)对 0 和二进制位做 XOR 运算，得到的仍然是这个二进制位
　a⊕0=a

```
class Solution:
    def singleNumber(self, nums: List[int]) -> int:
        a=0
        for i in nums:
            a^=i
        return a
```
