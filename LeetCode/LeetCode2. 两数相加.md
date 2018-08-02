# 2. 两数相加
## 题目
给定两个非空链表来表示两个非负整数。位数按照逆序方式存储，它们的每个节点只存储单个数字。将两数相加返回一个新的链表。

你可以假设除了数字 0 之外，这两个数字都不会以零开头。

## eg1

输入：(2 -> 4 -> 3) + (5 -> 6 -> 4)
输出：7 -> 0 -> 8
原因：342 + 465 = 807


## eg2


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
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        
    	}
	};

## 解法一
1. 把链表转换为整型值，然后将两个整型值加和再转换回链表

**这种方法不可行，当链表过长时会导致越界**


## 解法2
1. 按位加和，大于10进位
2. 定义flag代表是否有进位 flag = 1代表有进位，flag=0代表无进位

假设l1的长度大于l2，先将l1与l2相同长度的部分加和处理

再循环判定l1中的剩余部分，判断剩余部分时，如果出现flag=0的情况，就吧l1之后的部分直接连在结果链表上就可以了

最后需要判断flag是否为1，处理[1,9] [9]（结果为100）的情况

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
	    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
	        ListNode* head = new ListNode(0);
	        ListNode* a = head;
	        int flag = 0;
	        while(l1 != NULL && l2 != NULL)
	        {
	            int sum = l1->val + l2->val + flag;
	            if(sum >= 10)
	            {
	                ListNode* temp = new ListNode(sum % 10);
	                a->next = temp;
	                a = a->next;
	                flag = 1;
	            }
	            else
	            {
	                ListNode* temp = new ListNode(sum);
	                a->next = temp;
	                a = a->next;
	                flag = 0;
	            }
	            l1 = l1->next;
	            l2 = l2->next;
	        }
	        
	        if(l1 != NULL)
	        {
	            while(l1 != NULL)
	            {
	                int sum = l1->val + flag;
	                if(sum >= 10)
	                {
	                    ListNode* temp = new ListNode(sum % 10);
	                    a->next = temp;
	                    a = a->next;
	                    flag = 1;
	                    l1 = l1->next;
	                }
	                else
	                {
	                    ListNode* temp = new ListNode(sum);
	                    a->next = temp;
	                    a = a->next;
	                    flag = 0;
	                    a->next = l1->next;
	                    break;
	                }
	            }
	        }
	        
	        else if(l2 != NULL)
	        {
	            while(l2 != NULL)
	            {
	                int sum = l2->val + flag;
	                if(sum >= 10)
	                {
	                    ListNode* temp = new ListNode(sum % 10);
	                    a->next = temp;
	                    a = a->next;
	                    flag = 1;
	                    l2 = l2->next;
	                }
	                else
	                {
	                    ListNode* temp = new ListNode(sum);
	                    a->next = temp;
	                    a = a->next;
	                    flag = 0;
	                    a->next = l2->next;
	                    break;
	                }
	            }
	        }
	        
	        if(flag == 1)
	        {
	            ListNode* temp = new ListNode(1);
	            a->next = temp;
	        }
	        
	        return head->next;
	    }
	};

---
