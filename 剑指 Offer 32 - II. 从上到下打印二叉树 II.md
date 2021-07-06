### 剑指 Offer 32 - II. 从上到下打印二叉树 II

* 从上到下按层打印二叉树，同一层的节点按从左到右的顺序打印，每一层打印到一行

* 例如:给定二叉树: [3,9,20,null,null,15,7]，返回其层次遍历结果：
```
    3
   / \
  9  20
    /  \
   15   7

[
  [3],
  [9,20],
  [15,7]
]
```
> 考察的就是树的层次遍历，通常，我们都会用队列的思想来实现：

```
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
func levelOrder(root *TreeNode) [][]int {
    res := [][]int{}
    if root == nil {
        return res
    }

    //创建队列
    queue := []*TreeNode{root}
    level := 0
    //队列中还有元素则继续遍历
    for len(queue) != 0 {
        //利用临时队列保存左右节点
        tmp := []*TreeNode{}
        //创建当前高度的节点数组
        res = append(res, []int{})
        for _, v := range queue {
            //当前节点值，加入本高度数组
            res[level] = append(res[level], v.Val)
            //如果左节点不为空，将左节点加入临时队列中
            if v.Left != nil {
                tmp = append(tmp, v.Left)
            }
            //如果右节点不为空，将右节点加入临时队列中
            if v.Right != nil {
                tmp = append(tmp, v.Right)
            }
        }
        //当前遍历的高度+1
        level ++
        queue = tmp
    }
    return res
}
```
