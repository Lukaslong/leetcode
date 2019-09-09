## Merge Two Lists/合并两个有序链表
### 问题描述：
将两个有序链表合并为一个新的有序链表并返回。新链表是通过拼接给定的两个链表的所有节点组成的。 

##### 示例：

输入：1->2->4, 1->3->4

输出：1->1->2->3->4->4

问题链接：https://leetcode-cn.com/problems/merge-two-sorted-lists

--------------------
### 问题分析：
由于输入的链表均为有序链表，因此一次遍历两个链表即可，依次比较两个链表的value。

需要注意的是两个链表的长度可能不同，因此最后需要把剩下的链表“链接”上去。
```
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def mergeTwoLists(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        c1,c2=l1,l2
        rc=ListNode(0)
        rlistnode=rc
        while c1 and c2:
            if c1.val<=c2.val:
                rc.next=ListNode(c1.val)
                c1=c1.next
            else:
                rc.next=ListNode(c2.val)
                c2=c2.next
            rc=rc.next
        rc.next=c1 if c1 else c2
        return rlistnode.next
```