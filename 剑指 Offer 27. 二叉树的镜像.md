### 剑指 Offer 27. 二叉树的镜像

* 请完成一个函数，输入一个二叉树，该函数输出它的镜像
> 例如输入：
```
     4
   /   \
  2     7
 / \   / \
1   3 6   9
镜像输出：

     4
   /   \
  7     2
 / \   / \
9   6 3   1
```

> 输入：root = [4,2,7,1,3,6,9]

> 输出：[4,7,2,9,6,3,1]

```
//递归解法
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
func mirrorTree(root *TreeNode) *TreeNode {
    if root == nil {
        return nil
    }
    //获得根节点的左节点的处理结果
    left := mirrorTree(root.Left)
    //获得根节点的右节点的处理结果
    right := mirrorTree(root.Right)
    //交换并返回
    root.Left = right
    root.Right = left
    return root
}
```
