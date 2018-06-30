# 141. 环形链表
## 题目
给定一个链表，判断链表中是否有环 

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
	    bool hasCycle(ListNode *head) {
	        
	    }
	};

## 正确解法
- 此题是快慢指针的经典应用
- 定义快慢指针，每次迭代慢指针走一步，快指针走两步，如果存在环，快慢指针肯定会相遇，相遇就返回
- 如果快指针迭代结束还没相遇，那就说明没有环

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
	    bool hasCycle(ListNode *head) {
	        ListNode *slow = head;
	        ListNode *fast = head;
	        while(fast != NULL && fast->next != NULL)
	        {
	            slow = slow->next;
	            fast = fast->next->next;
	            if(slow == fast) return true;
	        }
	        return false;
	    }
	};
---