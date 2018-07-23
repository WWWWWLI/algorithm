# 13. 罗马数字转整数
## 题目
罗马数字包含以下七种字符：I， V， X， L，C，D 和 M。

	字符          数值
	I             1
	V             5
	X             10
	L             50
	C             100
	D             500
	M             1000

例如， 罗马数字 2 写做 II ，即为两个并列的 1。12 写做 XII ，即为 X + II 。 27 写做  XXVII, 即为 XX + V + II 。

通常情况下，罗马数字中小的数字在大的数字的右边。但也存在特例，例如 4 不写做 IIII，而是 IV。数字 1 在数字 5 的左边，所表示的数等于大数 5 减小数 1 得到的数值 4 。同样地，数字 9 表示为 IX。这个特殊的规则只适用于以下六种情况：

- I 可以放在 V (5) 和 X (10) 的左边，来表示 4 和 9。
- X 可以放在 L (50) 和 C (100) 的左边，来表示 40 和 90。 
- C 可以放在 D (500) 和 M (1000) 的左边，来表示 400 和 900。

给定一个罗马数字，将其转换成整数。输入确保在 1 到 3999 的范围内。

## eg1
输入: "III"
输出: 3

## eg2
输入: "IV"
输出: 4

## eg3
输入: "IX"
输出: 9

## eg4
输入: "LVIII"
输出: 58
解释: C = 100, L = 50, XXX = 30, III = 3.

## eg5
输入: "MCMXCIV"
输出: 1994
解释: M = 1000, CM = 900, XC = 90, IV = 4.

## 默认代码模板
	class Solution {
	public:
	    int romanToInt(string s) {
	        
	    }
	};

## 正确解法
1. 如果当前数字是最后一个数字，或者之后的数字比它小的话，则加上当前数字
2. 其他情况则减去这个数字
---
	class Solution {
	public:
	    int romanToInt(string s) {
	        map<char, int> m;
	        m.insert(pair<char, int>('I', 1));
	        m.insert(pair<char, int>('V', 5));
	        m.insert(pair<char, int>('X', 10));
	        m.insert(pair<char, int>('L', 50));
	        m.insert(pair<char, int>('C', 100));
	        m.insert(pair<char, int>('D', 500));
	        m.insert(pair<char, int>('M', 1000));
	        
	        int sum = 0;
	        
	        for(int i = 0; i < s.size() - 1; i++)
	        {
	            if(m[s[i]] >= m[s[i + 1]]) sum += m[s[i]];
	            else sum -= m[s[i]];
	        }
	        
	        sum += m[s[s.size() - 1]];
	        return sum;
	    }
	}; 
---