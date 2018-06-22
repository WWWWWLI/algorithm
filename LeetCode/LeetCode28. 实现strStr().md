# 28. 实现strStr()
## 题目
实现 strStr() 函数。

给定一个 haystack 字符串和一个 needle 字符串，在 haystack 字符串中找出 needle 字符串出现的第一个位置 (从0开始)。如果不存在，则返回  -1。

## eg1

输入: haystack = "hello", needle = "ll"
输出: 2

## eg2

输入: haystack = "aaaaa", needle = "bba"
输出: -1

## 默认代码模板

	class Solution {
	public:
	    int strStr(string haystack, string needle) {
	        
	    }
	};

## 正确解法
1. 先构造next数组[https://www.cnblogs.com/Mr-mwcss/p/5500946.html](https://www.cnblogs.com/Mr-mwcss/p/5500946.html)
2. 然后根据next匹配
3. 在匹配的时候需要区分两种情况
3.1 当第一个字母就不匹配时，需要将长串++
3.2 当其他字母不匹配时，需要回溯

**其实1和2是类似的**

---
	class Solution {
	public:
		int strStr(string haystack, string needle) {
			if (needle.size() == 0) return 0;
			if (haystack.size() == 0 && needle.size() > 0) return -1;
	
			//实现next数组 https://www.cnblogs.com/Mr-mwcss/p/5500946.html
			vector<int> next;
			next.push_back(-1);
			next.push_back(0);
			for (int k = 2; k < needle.size(); k++)
			{
				int i = k - 1;
				if (needle[next[i]] == needle[i])
				{
					next.push_back(next[k - 1] + 1);
				}
				else
				{
					while (1)
					{
						int j = i;
						i = next[i];
						if (needle[i] == needle[k - 1])
						{
							next.push_back(next[j] + 1);
							break;
						}
						if (next[i] == -1)
						{
							next.push_back(0);
							break;
						}
					}
				}
			}
	
			//实现KMP算法
	
			int i = 0;
			int j = 0;
			while (1)
			{
				if (haystack[i] == needle[j])
				{
					i++;
					j++;
					if (j == needle.size()) return i - needle.size();
				}
				else
				{
					if (next[j] == -1) i++;
					else
					{
						j = next[j];
					}
				}
				if (i == haystack.size()) return -1;
			}
		}
	};
---