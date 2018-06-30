# 234. 回文链表
## 题目
请判断一个链表是否为回文链表。
## eg1
输入: 1->2
输出: false

## eg2
输入: 1->2->2->1
输出: true

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
	    bool isPalindrome(ListNode* head) {
	        
	    }
	};

## 正确解法
1. 对于一般来说，可以将链表的值存入数组，判断数组是否为回文数组
2. 可以用快慢指针的方法，将链表的后一半反转，然后顺序判断即可
**注意：使用快慢指针的方法需要对于奇偶个数分别判断**

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
	    bool isPalindrome(ListNode* head) {
	        ListNode* fast = head;
	        ListNode* slow = head;
	        while(fast != NULL && fast->next != NULL)
	        {
	            slow = slow->next;
	            fast = fast->next->next;
	        }
	        
	        //偶数个节点
	        if(fast == NULL) slow = reverseList(slow);
	        //奇数个节点
	        else if(fast->next == NULL) slow = reverseList(slow->next);
	        
	        while(slow != NULL)
	        {
	            if(head->val != slow->val) return false;
	            else
	            {
	                head = head->next;
	                slow = slow->next;
	            }
	        }
	        return true;
	    }
	    
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