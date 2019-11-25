## hasCycle/环形链表
### 问题描述：
给定一个链表，判断链表中是否有环。

为了表示给定链表中的环，我们使用整数 pos 来表示链表尾连接到链表中的位置（索引从 0 开始）。 如果 pos 是 -1，则在该链表中没有环。

**示例 1：**
输入：head = [3,2,0,-4], pos = 1
输出：true
解释：链表中有一个环，其尾部连接到第二个节点。

![avatar](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/07/circularlinkedlist.png)

**示例 2：**
输入：head = [1,2], pos = 0
输出：true
解释：链表中有一个环，其尾部连接到第一个节点。

![avatar](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/07/circularlinkedlist_test2.png)

**示例 3：**
输入：head = [1], pos = -1
输出：false
解释：链表中没有环。

![avatar](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/07/circularlinkedlist_test3.png)

问题链接：https://leetcode-cn.com/problems/linked-list-cycle

------
## 问题分析：
哈希表的应用，不要被pos迷惑，这只是测试用例的输入，对于程序暂无用处。
Python中常用的哈希表主要是dict和set，这里使用dict，直接结点head作为字典的key，head.val作为字典的value。

```
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def hasCycle(self, head: ListNode) -> bool:
        dic={}
        while head:
            if head in dic:
                return True
            else:
                dic[head]=head.val
            head=head.next
        return False 
```