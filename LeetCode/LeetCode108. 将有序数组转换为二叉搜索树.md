# 108. 将有序数组转换为二叉搜索树
## 题目
将一个按照升序排列的有序数组，转换为一棵高度平衡二叉搜索树。

本题中，一个高度平衡二叉树是指一个二叉树每个节点 的左右两个子树的高度差的绝对值不超过 1。

## eg1
给定有序数组: [-10,-3,0,5,9],

一个可能的答案是：[0,-3,9,-10,null,5]，它可以表示下面这个高度平衡二叉搜索树：
![](https://i.imgur.com/kPtScfb.jpg)
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
	    TreeNode* sortedArrayToBST(vector<int>& nums) {
	       
	    }
	};

## 正确解法
- 平衡二叉搜索树的根结点的值正好是所有节点值的中间值，即中序遍历时，根结点位于正中间（因为是平滑二叉树）（如果是偶数个结点，则位于最中间两个靠前的那个）

- 使用二分法，先把有序数组的最中间值设为根结点，然后根结点的左孩子是左半段数组的最中间值，根结点的右孩子是右半段数组的最中间值。依次这样，即可以建立一个平衡二叉搜索树。

- 具体实现利用递归的思想

- 根节点应该是有序数组的中间点，从中间点分开为左右两个有序数组，在分别找出其中间点作为原中间点的左右两个子节点
- 递归结束条件是begin > end


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
	    TreeNode* sortedArrayToBST(vector<int>& nums) {
	        //if(nums.size() == 0) return NULL;
	        TreeNode* root = binary(nums, 0, nums.size() - 1);
	        return root;
	    }
	    
	    TreeNode* binary(vector<int>& nums, int begin, int end)
	    {
	        if(begin > end) return NULL;
	        int mid = (begin + end) / 2;
	        TreeNode* node = new TreeNode(nums[mid]);
	        node->left = binary(nums, begin, mid - 1);
	        node->right = binary(nums, mid + 1, end);
	        return node;
	    }
	};
---