# 102. 二叉树的层次遍历
## 题目
给定一个二叉树，返回其按层次遍历的节点值。 （即逐层地，从左到右访问所有节点）。




## eg1
例如:
给定二叉树: [3,9,20,null,null,15,7],
![](https://i.imgur.com/Ovu12El.jpg)
返回其层次遍历结果：
[
  [3],
  [9,20],
  [15,7]
]
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
	    vector<vector<int>> levelOrder(TreeNode* root) {
	       
	    }
	};

## 正确解法
- 利用队列实现
- 初始化时把根节点加入队列
- 然后输出队头元素，将队头元素的左右孩子入队
- 直至队为空为止

上述得到的结果输出的是一维遍历结果，如果要实现二维输出（如题所示）的话：
- 需要利用temp变量暂存某一层的队列
- 然后遍历temp，将temp中元素的左右孩子加入队列
- 每次遍历完temp将得到的一维结果push_back到最终结果中


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
	    vector<vector<int>> levelOrder(TreeNode* root) {
	        vector<vector<int>> order;
	        if(root == NULL) return order;
	        vector<int> alevel;
	        vector<TreeNode*> queue;
	        queue.push_back(root);
	        while(queue.size() != 0)
	        {
	            vector<TreeNode*> temp = queue;
	            queue.clear();
	            vector<TreeNode*>::iterator it = temp.begin();
	            while(it != temp.end())
	            {
	                alevel.push_back((*it)->val);
	                if((*it)->left != NULL) queue.push_back((*it)->left);
	                if((*it)->right != NULL) queue.push_back((*it)->right);
	                it++;
	            }
	            order.push_back(alevel);
	            alevel.clear();
	        }
	        return order;
	    }
	};
---