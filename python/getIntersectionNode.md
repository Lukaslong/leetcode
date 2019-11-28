## getIntersectionNode/相交链表
### 问题描述：
编写一个程序，找到两个单链表相交的起始节点。

如下面的两个链表：

![avatar](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/14/160_statement.png)

在节点 c1 开始相交。

注意：

如果两个链表没有交点，返回 null.
在返回结果后，两个链表仍须保持原有的结构。
可假定整个链表结构中没有循环。
程序尽量满足 O(n) 时间复杂度，且仅用 O(1) 内存。

问题链接：https://leetcode-cn.com/problems/intersection-of-two-linked-lists

### 问题分析：
1.最简单粗暴的方式是利用里外两个循环，即对headA中每个节点，遍历headB整个链表，并判断是否存在相同的节点。
此方法时间复杂度O(mn)，空间复杂度O(1)，不是很推荐的解法，这里就不放代码了。

2.进阶的做法是使用哈希表，如字典，先将链表A中的节点放到字典中，然后遍历链表B中的节点，并判断链表B中节点是否在字典中。
时间复杂度O(m+n)，空间复杂度O(m)或O(n)
```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def getIntersectionNode(self, headA: ListNode, headB: ListNode) -> ListNode:
        d={}
        while headA:
            d[headA]=headA.val
            headA=headA.next
        while headB:
            if headB in d:
                return headB
            else:
                headB=headB.next
        return headB
```

3.最后，还有双指针法，也是本题最巧妙的解法。
使两个链表到达相等位置时走过的是相同的距离。
假设链表A在交点前的长度为x1，链表B在交点前的长度为x2，相同部分长度y。
同时遍历链表A和链表B，到达末尾时，再指向另一个链表。
则当两链表走到相等的位置时：x1+y+x2 = x2+y+x1
时间复杂度O(m+n)，空间复杂度O(1)

```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def getIntersectionNode(self, headA: ListNode, headB: ListNode) -> ListNode:
        p=headA
        q=headB
        while p!=q:
            p=p.next if p else headB
            q=q.next if q else headA
        return p
```