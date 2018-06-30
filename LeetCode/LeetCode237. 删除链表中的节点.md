# 88. 合并两个有序数组
## 题目
请编写一个函数，使其可以删除某个链表中给定的（非末尾）节点，你将只被给定要求被删除的节点。

现有一个链表 -- head = [4,5,1,9]，它可以表示为:
 4 -> 5 -> 1 -> 9

## eg1
输入: head = [4,5,1,9], node = 5
输出: [4,1,9]
解释: 给定你链表中值为 5 的第二个节点，那么在调用了你的函数之后，该链表应变为 4 -> 1 -> 9.

## eg2
输入: head = [4,5,1,9], node = 1
输出: [4,5,9]
解释: 给定你链表中值为 1 的第三个节点，那么在调用了你的函数之后，该链表应变为 4 -> 5 -> 9.

说明:

- 链表至少包含两个节点。
- 链表中所有节点的值都是唯一的。
- 给定的节点为非末尾节点并且一定是链表中的一个有效节点。
- 不要从你的函数中返回任何结果。


## 默认代码模板
	/**
	 * Definition for singly-linked list.
	 * struct ListNode {
	 *     int val;
	 *     ListNode *next;
	 *     ListNode(int x) : val(x), next(NULL) {}
	 * };
	 */
	class Solution {
	public:
	    void deleteNode(ListNode* node) {
	        
	    }
	};

## 正确解法
这道题没给节点，也没给链表，只给了要删除的点
利用巧妙的方法，将下一个节点的值赋值给这个节点
然后删除下一个节点，完成这个节点的删除操作

---
	/**
	 * Definition for singly-linked list.
	 * struct ListNode {
	 *     int val;
	 *     ListNode *next;
	 *     ListNode(int x) : val(x), next(NULL) {}
	 * };
	 */
	class Solution {
	public:
	    void deleteNode(ListNode* node) {
	        //注意，这道题没给节点，也没给链表，只给了要删除的点
	        //利用巧妙的方法，将下一个节点的值赋值给这个节点
	        //然后删除下一个节点，完成这个节点的删除操作
	        node->val = node->next->val;
	        node->next = node->next->next;
	    }
	};
---