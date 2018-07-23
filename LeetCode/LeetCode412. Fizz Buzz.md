# 412. Fizz Buzz
## 题目
写一个程序，输出从 1 到 n 数字的字符串表示。

1. 如果 n 是3的倍数，输出“Fizz”；

2. 如果 n 是5的倍数，输出“Buzz”；

3. 如果 n 同时是3和5的倍数，输出 “FizzBuzz”。

## eg1
n = 15,

返回:
	[
	    "1",
	    "2",
	    "Fizz",
	    "4",
	    "Buzz",
	    "Fizz",
	    "7",
	    "8",
	    "Fizz",
	    "Buzz",
	    "11",
	    "Fizz",
	    "13",
	    "14",
	    "FizzBuzz"
	]
## 默认代码模板
	class Solution {
	public:
	    vector<string> fizzBuzz(int n) {
	       
	    }
	};

## 正确解法
- 一个循环加上判断
- 先判断能被3和5同时整除的情况
- 当都不能被整除时，将数字加入数组
- int转string可以用to_string函数


---
	class Solution {
	public:
	    vector<string> fizzBuzz(int n) {
	        vector<string> s;
	        for(int i = 1; i <= n; i++)
	        {
	            if(i % 3 == 0 && i % 5 == 0) s.push_back("FizzBuzz");
	            else if(i % 3 == 0 && i % 5 != 0) s.push_back("Fizz");
	            else if(i % 3 != 0 && i % 5 == 0) s.push_back("Buzz");
	            else s.push_back(to_string(i));
	        }
	        return s;
	    }
	};
---