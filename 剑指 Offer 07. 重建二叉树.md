### 剑指 Offer 07. 重建二叉树

* 输入某二叉树的前序遍历和中序遍历的结果，请构建该二叉树并返回其根节点。假设输入的前序遍历和中序遍历的结果中都不含重复的数字。

![](https://assets.leetcode.com/uploads/2021/02/19/tree.jpg)

> Input: preorder = [3,9,20,15,7], inorder = [9,3,15,20,7]

> Output: [3,9,20,null,null,15,7]

```
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
func buildTree(preorder []int, inorder []int) *TreeNode {
    for k := range inorder {
        if inorder[k] == preorder[0] {
            return &TreeNode{
                Val:    preorder[0],
                Left:   buildTree(preorder[1:k+1], inorder[0:k]),
                Right:  buildTree(preorder[k+1:], inorder[k+1:]),
            }
        }
    }
    return nil
}
```

