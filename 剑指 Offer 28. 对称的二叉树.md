### 剑指 Offer 28. 对称的二叉树

```
请实现一个函数，用来判断一棵二叉树是不是对称的。如果一棵二叉树和它的镜像一样，那么它是对称的。

例如，二叉树 [1,2,2,3,4,4,3] 是对称的。

    1
   / \
  2   2
 / \ / \
3  4 4  3
但是下面这个 [1,2,2,null,3,null,3] 则不是镜像对称的:

    1
   / \
  2   2
   \   \
   3    3
```

>输入：root = [1,2,2,3,4,4,3]

>输出：true

```
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
 //递归算法
func isSymmetric(root *TreeNode) bool {
    if root == nil {
        return true
    }

    return compare(root.Left, root.Right)
}
、、递归比较
func compare(a, b *TreeNode) bool {
        if a == nil && b == nil {
            return true
        }
        if (a!=nil && b==nil) || (a==nil && b!=nil) || (a.Val != b.Val) {
            return false
        }
        return compare(a.Left, b.Right) && compare(b.Left, a.Right)
    }

---------------------------------------------
---------------------------------------------
//中序遍历，两端比较算法
var ansArray []Node

type Node struct {
    val     int
    deep    int
}

func isSymmetric(root *TreeNode) bool {
    ansArray = make([]Node, 0)
    dfs(root, 0)

    anslen := len(ansArray)
    center := anslen / 2
    for i:=0; i<center; i++{
        if ansArray[i].val != ansArray[anslen-1-i].val || ansArray[i].deep != ansArray[anslen-1-i].deep {
			return false
		}
    }

    return true
}

//中序遍历算法的实现
func dfs(root *TreeNode, deep int) {
    if root == nil {
        return
    }
    dfs(root.Left, deep + 1)
    ansArray = append(ansArray, Node{val:root.Val, deep:deep})
    dfs(root.Right, deep + 1)
} 
```
