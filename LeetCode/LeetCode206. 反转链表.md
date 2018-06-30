# 206. 反转链表
## 题目
反转一个单链表。
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
	    ListNode* reverseList(ListNode* head) {
	        
	    }
	};

## 正确解法
分三种情况
1. 链表没有节点的情况
2. 链表只有一个节点的情况
3. 链表节点数量大于等于2的情况

- 没有节点直接返回
- 只有一个节点也直接返回
- 大于等于2个节点的时候需要利用三个指针来完成遍历

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
	    ListNode* reverseList(ListNode* head) {
	        //处理链表没有节点的情况
	        if(head == NULL) return head;
	        
	        //处理链表只有一个节点的情况
	        ListNode* n = head->next;
	        if(n == NULL) return head;
	        
	        //处理链表节点数量大于等于2的情况
	        ListNode* n_next = head->next->next;
	        ListNode* n_pre = head;
	        while(n_next != NULL)
	        {
	            n->next = n_pre;
	            n_pre = n;
	            n = n_next;
	            n_next = n_next->next;
	        }
	        n->next = n_pre;
	        head->next = NULL;
	        return n;
	    }
	};
---