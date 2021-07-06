### 剑指 Offer 25. 合并两个排序的链表

* 输入两个递增排序的链表，合并这两个链表并使新链表中的节点仍然是递增排序的

* 示例：
> 输入：1->2->4, 1->3->4
> 
> 输出：1->1->2->3->4->4

```
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
 
func mergeTwoLists(l1 *ListNode, l2 *ListNode) *ListNode {
    p := &ListNode{
        Val: 0,
        Next: nil,
    }
    res := p

    //如果两个都是空直接返回空
    if l1 == nil && l2 == nil {
        return nil
    }
 
    //两个都不为空时
    for l1 != nil && l2 != nil {
        if l1.Val < l2.Val {
            res.Next = l1
            l1 = l1.Next
        } else {
            res.Next = l2
            l2 = l2.Next
        }
        res = res.Next
    }

    if l1 != nil {
        res.Next = l1
    }

    if l2 != nil {
        res.Next = l2
    }

    return p.Next
}

//递归解法
func mergeTwoLists(l1 *ListNode, l2 *ListNode) *ListNode {
    if l1 == nil {
        return l2
    }
    if l2 == nil {
        return l1
    }

    var n *ListNode
    if l1.Val < l2.Val {
        n = l1
        n.Next = mergeTwoLists(l1.Next, l2)
    } else {
        n = l2
        n.Next = mergeTwoLists(l1, l2.Next)
    }
    return n 
}
```
