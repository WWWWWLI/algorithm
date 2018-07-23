# 326. 3的幂
## 题目
给定一个整数，写一个函数来判断它是否是 3 的幂次方。

## eg1
输入: 27
输出: true

## eg2
输入: 0
输出: false

## eg3
输入: 9
输出: true

## eg4
输入: 45
输出: false

## 默认代码模板
	class Solution {
	public:
	    bool isPowerOfThree(int n) {
	        
	    }
	};

## 正确解法
---
	class Solution {
	public:
	    bool isPowerOfThree(int n) {
	        if(n == 1) return true;
	        else if(n == 0) return false;
	        else if(n % 3 == 0)
	        {
	            return isPowerOfThree(n / 3);
	        }
	        else return false;
	    }
	};
---