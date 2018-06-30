# 19. 删除链表的倒数第N个节点
## 题目
给定一个链表，删除链表的倒数第 n 个节点，并且返回链表的头结点。
## eg1
给定一个链表: 1->2->3->4->5, 和 n = 2.

当删除了倒数第二个节点后，链表变为 1->2->3->5.

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
	    ListNode* removeNthFromEnd(ListNode* head, int n) {
	        
	    }
	};

## 正确解法
- 这道题的边界条件非常烦人，分为三种情况，删除的是链表第一个节点，最后一个节点，中间节点
- 第一个节点：

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
	    ListNode* removeNthFromEnd(ListNode* head, int n) {
	        ListNode* node = head;
	        //删除的是第一个节点
	        for(int i = 0; i < n; i++)
	        {
	            node = node->next;
	        }
	        if(node == NULL)
	        {
	            head = head->next;
	            return head;
	        }
	        
	        
	        ListNode* node_del = head;
	        while(node->next != NULL)
	        {
	            node = node->next;
	            node_del = node_del->next;
	        }
	        
	        //删除的是最后一个节点
	        if(n == 1)
	        {
	            node_del->next = NULL;
	            return head;
	        }
	        
	        //删除的是中间节点
	        else
	        {
	            node_del->next->val = node_del->next->next->val;
	            node_del->next->next = node_del->next->next->next;
	            return head;
	        }
	    }
	};
---