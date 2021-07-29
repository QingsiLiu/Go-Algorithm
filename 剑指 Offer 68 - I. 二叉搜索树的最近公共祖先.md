### 剑指 Offer 68 - I. 二叉搜索树的最近公共祖先

* 给定一个二叉搜索树, 找到该树中两个指定节点的最近公共祖先

> 例如，给定如下二叉搜索树:  root = [6,2,8,0,4,7,9,null,null,3,5]

![](https://assets.leetcode-cn.com/aliyun-lc-upload/uploads/2018/12/14/binarysearchtree_improved.png)

```
输入: root = [6,2,8,0,4,7,9,null,null,3,5], p = 2, q = 8
输出: 6 
解释: 节点 2 和节点 8 的最近公共祖先是 6。
```

不知道为啥力扣上没有允许golang语言的编译环境

```
******C++******
class Solution {
public:
    TreeNode* lowestCommonAncestor(TreeNode* root, TreeNode* p, TreeNode* q) {
        if (p->val < root->val && q->val < root->val) {
		    return lowestCommonAncestor(root->left, p, q);
	    }

    	if (root->val < p->val && root->val < q->val) {
	    	return lowestCommonAncestor(root->right, p, q);
	    }

	    return root;
    }
};


******golang******
func lowestCommonAncestor(root, p, q *TreeNode) (ancestor *TreeNode) {
    ancestor = root
    for{
        if ancestor.val > p.val && ancestor.val > q.val {
            ancestor = ancestor.left
        } else if ancestor.val < p.val && ancestor.val < q.val {
            ancestor = ancestor.right
        } else {
            return
        }
    }
}
```













