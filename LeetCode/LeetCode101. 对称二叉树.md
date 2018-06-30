# 101. 对称二叉树
## 题目
给定一个二叉树，检查它是否是镜像对称的。

例如，二叉树 [1,2,2,3,4,4,3] 是对称的。
![](https://i.imgur.com/d1FjyMD.jpg)

但是下面这个 [1,2,2,null,3,null,3] 则不是镜像对称的:
![](https://i.imgur.com/ZwBwvOg.jpg)
## 默认代码模板
	/**
	 * Definition for a binary tree node.
	 * struct TreeNode {
	 *     int val;
	 *     TreeNode *left;
	 *     TreeNode *right;
	 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
	 * };
	 */
	class Solution {
	public:
	    bool isSymmetric(TreeNode* root) {
	       
	    }
	};

## 正确解法
- 利用递归解决：**判断子树是否对称**

---
	/**
	 * Definition for a binary tree node.
	 * struct TreeNode {
	 *     int val;
	 *     TreeNode *left;
	 *     TreeNode *right;
	 *     TreeNode(int x) : val(x), left(NULL), right(NULL) {}
	 * };
	 */
	class Solution {
	public:
	    bool isSymmetric(TreeNode* root) {
	        if(root == NULL) return true;
	        else return symmetric(root->left, root->right);
	    }
	    
	    bool symmetric(TreeNode* lefttree, TreeNode* righttree)
	    {
	        if(lefttree == NULL && righttree == NULL) return true;
	        else if(lefttree != NULL && righttree != NULL)
	        {
	            if(lefttree->val == righttree->val) return symmetric(lefttree->left, righttree->right)  && symmetric(lefttree->right, righttree->left);
	            else return false;
	        }
	        else return false;
	    }
	};
---