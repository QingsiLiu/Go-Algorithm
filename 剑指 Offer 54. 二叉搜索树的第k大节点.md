### 剑指 Offer 54. 二叉搜索树的第k大节点

* 给定一棵二叉搜索树，请找出其中第k大的节点

> 输入: root = [3,1,4,null,2], k = 1
```
    3
   / \
   1  4
   \
    2
```
>输出: 4

```
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
func kthLargest(root *TreeNode, k int) int {
    res := []int{}
    inOrder(root, &res)
    return res[k-1]
}


func inOrder(root *TreeNode, count *[]int) {
    if root == nil {
        return 
    }

    inOrder(root.Right, count)
    *count = append(*count, root.Val)
    inOrder(root.Left, count)
}
```
