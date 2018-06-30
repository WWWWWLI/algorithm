# 98. 验证二叉搜索树
## 题目
给定一个二叉树，判断其是否是一个有效的二叉搜索树。

一个二叉搜索树具有如下特征：

- 节点的左子树只包含小于当前节点的数。
- 节点的右子树只包含大于当前节点的数。
- 所有左子树和右子树自身必须也是二叉搜索树。


## eg1
输入:
![](https://i.imgur.com/xRivt3e.jpg)
输出: true

## eg2
输入:
![](https://i.imgur.com/9FXwTjT.jpg)
输出: false
解释: 输入为: [5,1,4,null,null,3,6]。
根节点的值为 5 ，但是其右子节点值为 4 。
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
	    bool isValidBST(TreeNode* root) {
	       
	    }
	};

## 正确解法
- 二叉搜索树有效的等价于二叉树中序遍历序列有序
- 按照中序遍历二叉树，然后查看遍历序列是否有序
- 中序遍历按照递归实现**左子树 访问根 右子树(inordertraverse)**
- 每次**访问根**就把根的值插入向量
- **注意向量作为参数时传入的是引用格式(vector&lt;int&gt;& a)**
![](https://i.imgur.com/4TexjtF.png)
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
	    bool isValidBST(TreeNode* root) {
	        if(root == NULL) return true;
	        vector<int> a;
	        inordertraverse(root, a);
	        vector<int>::iterator it1 = a.begin();
	        vector<int>::iterator it2 = it1 + 1;
	        while(it2 != a.end())
	        {
	            if(*it1 < *it2)
	            {
	                it1++;
	                it2++;
	            }
	            else return false;
	        }
	        return true;
	        
	    }
	    
	    void inordertraverse(TreeNode* root, vector<int>& a)
	    {
	        if(root != NULL)
	        {
	            inordertraverse(root->left, a);
	            a.push_back(root->val);
	            inordertraverse(root->right, a);
	        }
	    }
	};
---