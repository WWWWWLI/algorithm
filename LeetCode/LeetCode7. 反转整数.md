# LeetCode7. 反转整数 
## 题目
给定一个 32 位有符号整数，将整数中的数字进行反转。

## eg1

输入: 123
输出: 321

## eg2

输入: -123
输出: -321

## eg3

输入: 120
输出: 21

## 默认代码模板

	class Solution {
	public:
	    int reverse(int x) {
	        
	    }
	};


## 解法

不断求余加和乘10

**注意**

1. 为了防止溢出，需要将和变量sum定义为长整型(long)，在判断结果时，如果没有溢出在强制转换成int型
2. C++中没有幂运算符，需要用到pow(2,20)计算2的20次方

---
	class Solution {
	public:
	    int reverse(int x) {
	        bool negative;
	        if(x > 0)
	        {
	            negative = false;
	        }
	        else if (x < 0)
	        {
	            negative = true;
	            x = -x;
	        }
	        else
	        {
	            return 0;
	        }
	        
	        long sum = 0;
	        int shang;
	        int yu;
	        while(1)
	        {
	            shang = x / 10;
	            yu = x % 10;
	            if(shang == 0)
	            {   
	                sum = sum + yu;
	                break;
	            }
	            else
	            {
	                sum = (sum + yu) * 10;
	            }
	            x = x / 10;
	        }
	        if(negative) sum = -sum;
	        if(sum < -pow(2, 31) || sum > pow(2, 31) - 1) return 0;
	        
	        return (int)sum;
	    }
	};
---