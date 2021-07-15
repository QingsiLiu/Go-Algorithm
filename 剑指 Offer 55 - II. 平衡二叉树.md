### 剑指 Offer 55 - II. 平衡二叉树

* 输入一棵二叉树的根节点，判断该树是不是平衡二叉树。如果某二叉树中任意节点的左右子树的深度相差不超过1，那么它就是一棵平衡二叉树
> 给定二叉树 [3,9,20,null,null,15,7], 返回 true 
```
    3
   / \
  9  20
    /  \
   15   7
```

```
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
func isBalanced(root *TreeNode) bool {
    if root == nil {
        return true
    }

    return abs(depth(root.Left)-depth(root.Right)) <= 1 && isBalanced(root.Left) && isBalanced(root.Right)
}

func depth(root *TreeNode) int {
    if root == nil {
        return 0
    }

    return max(depth(root.Left), depth(root.Right)) + 1
}

func max(x, y int) int {
    if x > y {
        return x
    }
    return y
}

func abs(x int) int {
    if x < 0 {
        return -1 * x
    }
    return x
}
------------------------------------------------------------------
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
func isBalanced(root *TreeNode) bool {
    return height(root) >= 0
}

func height(root *TreeNode) int {
    if root == nil {
        return 0
    }
    left := height(root.Left)
    right := height(root.Right)
    if left == -1 || right == -1 || abs(left-right) > 1 {
        return -1
    }
    return max(left, right) + 1
}

func abs(x int) int {
    if x < 0 {
        return -1 * x
    }
    return x
}

func max(x, y int) int {
    if x > y {
        return x
    }
    return y
}
```












