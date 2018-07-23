# 3. 无重复字符的最长子串
## 题目

给定一个字符串，找出不含有重复字符的最长子串的长度。

## eg1
给定 "abcabcbb" ，没有重复字符的最长子串是 "abc" ，那么长度就是3。

给定 "bbbbb" ，最长的子串就是 "b" ，长度是1。

给定 "pwwkew" ，最长子串是 "wke" ，长度是3。请注意答案必须是一个子串，"pwke" 是 子序列  而不是子串。

## 默认代码模板

	class Solution {
		public:
    	int lengthOfLongestSubstring(string s) {
        
    	}
	};


## 解法一
1. string.substr(pos, i) string的pos位置之后i个组成的子串
2. string.find() 返回某个字符的位置pos

---

	class Solution {
	public:
	    int lengthOfLongestSubstring(string s) {
	        if(s.size() == 0) return 0;
	        if(s.size() == 1) return 1;
	        int max = 1;
	        int now = 1;
	        int i = 0;
	        int p = 0;
	        int j = 1;
	        while(j < s.size())
	        {
	            string temp = s.substr(i, j - i);
	            int pos = temp.find(s[j]);
	            if(pos == string::npos)
	            {
	                //没找到
	                j++;
	                now = j - i;
	                if(now > max) max = now;
	            }
	            else
	            {
	                i = i + pos + 1;
	                j++;
	                now = j - i;
	            }
	        }
	        return max;
	    }
	};

---
