# 38. 报数
## 题目
编写一个函数来查找字符串数组中的最长公共前缀。

如果不存在公共前缀，返回空字符串 ""。

## eg1

输入: ["flower","flow","flight"]
输出: "fl"
## eg2

输入: ["dog","racecar","car"]
输出: ""
解释: 输入不存在公共前缀。

## 默认代码模板

	class Solution {
	public:
	    string longestCommonPrefix(vector<string>& strs) {
	        
	    }
	};

## 正确解法
先找到最短的串
然后按照列循环
与最短的串比较
注意字符串集为空和最短串为空的情况（直接返回）
也要注意所有串都一样的情况（在循环外也要返回）

---
	class Solution {
	public:
	    string longestCommonPrefix(vector<string>& strs) {
	        //如果字符串集为空，则返回空串
	        if(strs.size() == 0) return "";
	        
	        //找到最短的字符串
	        int min_size = pow(2,20);
	        string min_string;
	        for(int i = 0; i < strs.size(); i++)
	        {
	            if(strs[i].size() < min_size)
	            {
	                min_size = strs[i].size();
	                min_string = strs[i];
	            }
	        }
	        
	        //如果最短的字符串为0返回空串
	        if(min_size == 0) return "";
	        
	        string s("");
	        
	        for(int j = 0; j < min_size; j++)
	        {
	            int i = 0;
	            for(; i < strs.size(); i++)
	            {
	                if(strs[i][j] != min_string[j]) return s;
	            }
	            s.push_back(min_string[j]);
	        }
	        return s;
	    }
	};
---