# LeetCode66.加一
## 题目
给定一个非负整数组成的非空数组，在该数的基础上加一，返回一个新的数组。

最高位数字存放在数组的首位， 数组中每个元素只存储一个数字。

你可以假设除了整数 0 之外，这个整数不会以零开头。

## eg1
输入: [1,2,3]

输出: [1,2,4]

解释: 输入数组表示数字 123。

## eg2
输入: [4,3,2,1]

输出: [4,3,2,2]

解释: 输入数组表示数字 4321。

## 默认代码模板

	class Solution {
	public:
	    vector<int> plusOne(vector<int>& digits) {
	        
	    }
	};


## 解法

先给最后一位加一

从数组最后一位(digits.end()-1)开始遍历

直到遍历至第一位(digits.begin())为止

判断当前位是否等于10

如果等于10的话，前一位加一，当前位归零

如果不等于10的话，直接跳出循环

所以说，跳出循环有两种方式，第一种是循环到digits.begin()了，第二种是遇到不为10的位没必要循环下去了

如果出现第一种情况的话，我们需要判断第一位是否为10

如果第一位为10的话，先将第一位赋值0，然后在最前插入一位1



---

	class Solution {
	public:
	    vector<int> plusOne(vector<int>& digits) {
	        vector<int>::iterator it = digits.end() - 1;
	        ++*it;
	        for(; it != digits.begin(); it--)
	        {
	            if(*it == 10)
	            {
	                ++*(it - 1);
	                *it = 0;
	            }
	            else break;
	        }
	        if(*it == 10)
	        {
	            *it = 0;
	            digits.insert(it, 1, 1);
	        }
	        return digits;
	    }
	};

---
