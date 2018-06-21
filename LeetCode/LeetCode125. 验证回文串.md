# LeetCode125. 验证回文串
## 题目
给定一个字符串，验证它是否是回文串，只考虑字母和数字字符，可以忽略字母的大小写。
**说明：**本题中，我们将空字符串定义为有效的回文串。
## eg1
输入: "A man, a plan, a canal: Panama"
输出: true

## eg2
输入: "race a car"
输出: false

## 默认代码模板

	class Solution {
	public:
	    bool isPalindrome(string s) {
	        
	    }
	};
## 正确解法

定义两个迭代器，分别从字符串开始与末尾进行遍历
如果遇到不是字母或数字的值，则跳过

**由于本题中需要包括数字，所以不能简单的通过ascii码进行字母大小写的忽略**
**本解法在判断字母是否相等之前，将大写全部转换为小写，实现忽略大小写**

---
	class Solution {
	public:
	    bool isPalindrome(string s) {
	        if(s.size() < 2) return true;
	        string::iterator it1 = s.begin();
	        string::iterator it2 = s.end() - 1;
	        for(; it1 != it2; )
	        {
	            if(!((*it1 >= '0' && *it1 <= '9') || (*it1 >= 'a' && *it1 <= 'z') || (*it1 >= 'A' && *it1 <= 'Z')))
	            {
	                it1++;
	                continue;
	            }
	            if(!((*it2 >= '0' && *it2 <= '9') || (*it2 >= 'a' && *it2 <= 'z') || (*it2 >= 'A' && *it2 <= 'Z')))
	            {
	                it2--;
	                continue;
	            }
	            if(*it1 >= 'A' && *it1 <= 'Z') *it1 = (char)(*it1 + 97 -65);
	            if(*it2 >= 'A' && *it2 <= 'Z') *it2 = (char)(*it2 + 97 -65);
	            if(*it1 == *it2)
	            {
	                it1++;
	                it2--;
	                if(it2 + 1 == it1) return true;
	            }
	            else return false;
	        }
	        return true;
	    }
	};
---