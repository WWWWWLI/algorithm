# 38. 报数
## 题目
报数序列是指一个整数序列，按照其中的整数的顺序进行报数，得到下一个数。其前五项如下：
1.     1
2.     11
3.     21
4.     1211
5.     111221

1 被读作  "one 1"  ("一个一") , 即 11。
11 被读作 "two 1s" ("两个一"）, 即 21。
21 被读作 "one 2",  "one 1" （"一个二" ,  "一个一") , 即 1211

给定一个正整数 n ，输出报数序列的第 n 项。

注意：整数顺序将表示为一个字符串。

## eg1

输入: 1
输出: "1"

## eg2

输入: 4
输出: "1211"

## 默认代码模板

	class Solution {
	public:
	    string countAndSay(int n) {
	        
	    }
	};

## 正确解法
1. 需要两个指针，一个指向A个B的B，另一个寻找下一个B
2. 因为需要两个指针，所以n小于等于2的时候直接返回就行了 
3. int 0-9转char方法：int+'0'

---
	class Solution {
	public:
		string countAndSay(int n) {
			if (n == 1) return "1";
			if (n == 2)
			{
				return "11";
			}
			string a("11");
			for (int i = 3; i <= n; i++)
			{
				int count = 1;
				string b(a);
				a.clear();
				int j = 0;
				int k = 1;
				while (1)
				{
					if (b[j] == b[k])
					{
						k++;
						count++;
						if (k == b.size())
						{
							a.push_back(count + '0');
							a.push_back(b[j]);
							break;
						}
					}
					else
					{
						a.push_back(count + '0');
						a.push_back(b[j]);
						count = 1;
						j = k;
						k++;
						if (k == b.size())
						{
							a.push_back(count + '0');
							a.push_back(b[j]);
							break;
						}
					}
				}
			}
			return a;
		}
	};
---