### 剑指 Offer 55 - I. 二叉树的深度

* 输入一棵二叉树的根节点，求该树的深度。从根节点到叶节点依次经过的节点（含根、叶节点）形成树的一条路径，最长路径的长度为树的深度

> 例如：给定二叉树 [3,9,20,null,null,15,7]，返回它的最大深度 3 。
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
func maxDepth(root *TreeNode) int {
    if root == nil {
        return 0
    }

    var count int = 1

    return max(help(root.Left, count), help(root.Right, count))
}

func help(root *TreeNode, count int) int {
    if root == nil {
        return count
    }

    if root.Left == nil && root.Right == nil {
        return count + 1
    }

    if root.Left != nil || root.Right != nil {
        return max(help(root.Left, count+1), help(root.Right, count+1))
    }

    return count
}

func max(x, y int) int {
    if x > y {
        return x
    }
    return y
}

-----------------------------------------------------------------

func maxDepth(root *TreeNode) int {
    if root == nil {
        return 0
    }

    return max(maxDepth(root.Left), maxDepth(root.Right)) + 1
}

func max(a, b int) int {
    if a > b {
        return a
    }
    return b
}

```
