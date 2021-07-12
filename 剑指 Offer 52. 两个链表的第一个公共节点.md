### 剑指 Offer 52. 两个链表的第一个公共节点

* 输入两个链表，找出它们的第一个公共节点:在节点 c1 开始相交。

![](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/14/160_statement.png)

```
/**
 * Definition for singly-linked list.
 * type ListNode struct {
 *     Val int
 *     Next *ListNode
 * }
 */
func getIntersectionNode(headA, headB *ListNode) *ListNode {
    tmpA, tmpB := headA, headB
    var lenA, lenB int
    for tmpA != nil {
        lenA ++
        tmpA = tmpA.Next
    }
    
    for tmpB != nil {
        lenB ++
        tmpB = tmpB.Next
    }

    a, b := headA, headB
    if lenA < lenB {
        tmp := lenB - lenA
        for i:=0; i<tmp; i++{
            b = b.Next
        }
    } else {
        tmp := lenA - lenB
        for i:=0; i<tmp; i++{
            a = a.Next
        }
    }

    for a != nil && b != nil {
        if a == b {
            return a
        }
        a = a.Next
        b = b.Next
    }

    return nil

}
```
