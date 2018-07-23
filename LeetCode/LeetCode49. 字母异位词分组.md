# 49. 字母异位词分组
## 题目
给定一个字符串数组，将字母异位词组合在一起。字母异位词指字母相同，但排列不同的字符串。

## eg1

	输入: ["eat", "tea", "tan", "ate", "nat", "bat"],
	输出:
	[
	  ["ate","eat","tea"],
	  ["nat","tan"],
	  ["bat"]
	]

## 规定

- 所有输入均为小写字母。
- 不考虑答案输出的顺序。


## 默认代码模板

	class Solution {
	public:
	    vector<vector<string>> groupAnagrams(vector<string>& strs) {
	        
	    }
	};

## 解法一
1. map的访问方法：m[key]访问key对应的value
2. 遍历map的方法map &lt; key类型, value类型 &gt; ::iterator = map.begin();
3. it->first代表key
4. it->second代表value

---

	class Solution {
	public:
	    vector<vector<string>> groupAnagrams(vector<string>& strs) {
	        vector<vector<string> > res;
	        map<string, vector<string>> m;
	        for(int i = 0; i < strs.size(); i++)
	        {
	            string temp = strs[i];
	            sort(temp.begin(), temp.end());
	            m[temp].push_back(strs[i]);
	        }
	        map<string, vector<string> >::iterator it = m.begin();
	        for(; it != m.end(); it++)
	        {
	            res.push_back(it->second);
	        }
	        return res;
	        
	    }
	};

---


