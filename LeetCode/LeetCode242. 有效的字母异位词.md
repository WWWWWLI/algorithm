# LeetCode48. 旋转图像
## 题目
给定两个字符串 s 和 t ，编写一个函数来判断 t 是否是 s 的一个字母异位词。
## eg

输入: s = "anagram", t = "nagaram"
输出: true

## eg2

输入: s = "rat", t = "car"
输出: false

**说明:**
你可以假设字符串只包含小写字母。

## 默认代码模板

	class Solution {
	public:
	    bool isAnagram(string s, string t) {
	        
	    }
	};
## 正确解法

利用两个数组分别记录字母及出现次数
分别比较两个数组的各个元素

---
	class Solution {
	public:
	    bool isAnagram(string s, string t) {
	        //初始化变量
	        string::iterator it = s.begin();
	        int ss[26] = {0};
	        int tt[26] = {0};
	        
	        //统计各个字符出现的次数
	        for(; it != s.end(); it++) ss[(int)(*it - 'a')]++;
	        it = t.begin();
	        for(; it != t.end(); it++) tt[(int)(*it - 'a')]++;
	        
	        //依次比较出现的个数
	        for(int i = 0; i < 26; i++)
	        {
	            if (ss[i] != tt[i]) return false; 
	        }
	        
	        return true;
	    }
	};
---