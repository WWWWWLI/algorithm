# 21. 合并两个有序链表
## 题目
将两个有序链表合并为一个新的有序链表并返回。新链表是通过拼接给定的两个链表的所有节点组成的。 
## eg1
输入：1->2->4, 1->3->4
输出：1->1->2->3->4->4

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
	    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
	        
	    }
	};

## 正确解法
- 如果l1 l2为空的话，直接返回另一个即可
- 声明一个空链表(head)
	- l1 <= l2 将l1加入空链表(head->next = l1)
	- l1 > l2 将l2加入空链表(head->next = l2)
- 最后判断一下剩余元素
- 注意保存head的头结点作为返回值

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
	    ListNode* mergeTwoLists(ListNode* l1, ListNode* l2) {
	        if(l1 == NULL) return l2;
	        if(l2 == NULL) return l1;
	        ListNode* head;
	        if(l1->val <= l2->val)
	        {
	            head = l1;
	            l1 = l1->next;
	        }
	        else
	        {
	            head = l2;
	            l2 = l2->next;
	        }
	        ListNode* headhead = head;
	        
	        while(l1 != NULL && l2 != NULL)
	        {
	            if(l1->val <= l2->val)
	            {
	                head->next = l1;
	                l1 = l1->next;
	            }
	            else
	            {
	                head->next = l2;
	                l2 = l2->next;
	            }
	            head = head->next;
	        }
	        if(l1 == NULL && l2 != NULL) head->next = l2;
	        else head->next = l1;
	        
	        return headhead;
	    }
	    
	};
---