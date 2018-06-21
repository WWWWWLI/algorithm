# LeetCode387. 字符串中的第一个唯一字符
## 题目
给定一个字符串，找到它的第一个不重复的字符，并返回它的索引。如果不存在，则返回 -1。

## eg

s = "leetcode"
返回 0.

s = "loveleetcode",
返回 2.

## 默认代码模板

	class Solution {
	public:
	    int firstUniqChar(string s) {
	        
	    }
	};


## 错误解法

利用两个迭代器，第一个迭代器遍历整个字符串，第二个迭代器从第一个迭代器后一个字符开始遍历

如果字符串是“cc”
正常来说应该返回-1
错误解法返回了1

**想算法一定要整体过一遍**

## 正确解法

利用一个整型长度为26的数组进行存储

	(int)(*it - 'a')获取位置

利用两个循环
第一个循环用来记录字符串各个字母出现了多少次
第二个循环依次查看字符串中的字符出现了多少次，找到第一个出现一次的字符，返回位置即可

---
	class Solution {
	public:
	    int firstUniqChar(string s) {
	        
	        string::iterator it = s.begin();
	        int a[26] = {0};
	        for(; it != s.end(); it++)
	        {
	           a[(int)(*it - 'a')]++;
	        }
	        
	        it = s.begin();
	        for(int i = 0; it != s.end(); it++)
	        {
	            if(a[(int)(*it - 'a')] == 1) return i;
	            else if(a[(int)(*it - 'a')] > 1) i++;
	        }
	        
	        return -1;
	    }
	};
---