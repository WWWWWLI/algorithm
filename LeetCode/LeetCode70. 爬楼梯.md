# 70.爬楼梯
## 题目
假设你正在爬楼梯。需要 n 步你才能到达楼顶。

每次你可以爬 1 或 2 个台阶。你有多少种不同的方法可以爬到楼顶呢？

注意：给定 n 是一个正整数。

## eg1
输入： 2
输出： 2
解释： 有两种方法可以爬到楼顶。
1.  1 步 + 1 步
2.  2 步

## eg2
输入： 3
输出： 3
解释： 有三种方法可以爬到楼顶。
1.  1 步 + 1 步 + 1 步
2.  1 步 + 2 步
3.  2 步 + 1 步


## 默认代码模板
	class Solution {
	public:
	    int climbStairs(int n) {
	        
	    }
	};

## 正确解法
- 设S(n)剩余n级台阶时走法的数量,则S(n) = S(n - 1) + S(n - 2)
- 初始条件为S(1) = 1, S(2) = 2
- 可以得到递推公式 


---
	class Solution {
	public:
	    int climbStairs(int n) {
	        vector<int> climb;
	        climb.push_back(1);
	        climb.push_back(2);
	        for(int i = 2; i < n; i++)
	        {
	            climb.push_back(climb[i - 2] + climb[i - 1]);
	        }
	        return climb[n - 1];
	    }
	};
---