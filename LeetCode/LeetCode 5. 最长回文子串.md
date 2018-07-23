# 5. 最长回文子串
## 题目
给定一个字符串 s，找到 s 中最长的回文子串。你可以假设 s 的最大长度为1000。

## eg1

输入: "babad"
输出: "bab"
注意: "aba"也是一个有效答案。

## eg2

输入: "cbbd"
输出: "bb"

## 默认代码模板

	class Solution {
		public:
    	string longestPalindrome(string s) {
        
    	}
	};

## 注意
1. 二重循环
2. 可以利用当前最长减少程序执行时间
3. 如果当前循环位置+当前最长长度>字符串长度，那就没必要继续循环了

## 解法

---

	class Solution {
	public:
	    string longestPalindrome(string s) {
	        int ll = 0;
	        string ls;
	        int i = 0;
	        int start = i;
	        while(i + ll < s.size()){
	            int j = i + ll;
	            for(;j < s.size(); j++){
	                string temp(s, i, j-i+1);
	                if(isPalindrome(temp)){
	                    if(ll < j-i+1){
	                        ll = j-i+1;
	                        start = i;
	                    }
	                }
	            }
	            i++;
	        }
	        return string(s, start, ll);
	    }
	
	    bool isPalindrome(string s){
	        if(s.size() == 0) return true;
	        int i = 0;
	        int j = s.size() - 1;
	        while(i < j){
	            if(s[i] == s[j]){
	                i++;
	                j--;
	            }
	            else return false;
	        }
	        return true;
	    }
	};

---