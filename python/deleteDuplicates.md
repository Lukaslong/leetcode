## deleteDuplicates/删除链表中重复元素
### 问题描述：
给定一个排序链表，删除所有重复的元素，使得每个元素只出现一次
##### 示例 1：
输入： 1->1->2

输出： 1->2

##### 示例 2:

输入: 1->1->2->3->3

输出: 1->2->3

问题链接：https://leetcode-cn.com/problems/remove-duplicates-from-sorted-list

--------
### 问题分析：
这里首先进行了输入链表为空的判断，否则当输入链表为空时，tmp.next=ListNode(head.val)将会报错。

创建一个临时链表tmp用来跟踪head，同时在开始也创建了ans链表用于返回输出链表的起点，否则最后tmp已经到链表尾部了，直接输出的话就只有最后一个节点了。

以上为链表问题比较通用的做法。

```
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def deleteDuplicates(self, head):
        """
        :type head: ListNode
        :rtype: ListNode
        """
        if not head:
            return head
        tmp=ListNode(head.val)
        ans=tmp
        head=head.next
        while head:
            if tmp.val!=head.val:
                tmp.next=ListNode(head.val)
                tmp=tmp.next
            head=head.next
        return ans
```
