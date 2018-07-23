# 198. 打家劫舍
## 题目
你是一个专业的小偷，计划偷窃沿街的房屋。每间房内都藏有一定的现金，影响你偷窃的唯一制约因素就是相邻的房屋装有相互连通的防盗系统，如果两间相邻的房屋在同一晚上被小偷闯入，系统会自动报警。

给定一个代表每个房屋存放金额的非负整数数组，计算你在不触动警报装置的情况下，能够偷窃到的最高金额。

## eg1
输入: [1,2,3,1]
输出: 4
解释: 偷窃 1 号房屋 (金额 = 1) ，然后偷窃 3 号房屋 (金额 = 3)。
偷窃到的最高金额 = 1 + 3 = 4 。

## eg2
输入: [2,7,9,3,1]
输出: 12
解释: 偷窃 1 号房屋 (金额 = 2), 偷窃 3 号房屋 (金额 = 9)，接着偷窃 5 号房屋 (金额 = 1)。
偷窃到的最高金额 = 2 + 9 + 1 = 12 。
## 默认代码模板
	class Solution {
	public:
	    int rob(vector<int>& nums) {
	        
	    }
	};

## 正确解法
- 定义数组g，g[i]代表偷窃第i间房的最高金额
- g[i] = max(g[i-1], g[i-2] + nums[i])
- g[0] = nums[0]
- g[1] = max(nums[0], nums[1])
- 根据以上递推公式可以得到最大金额
**求vector<int> a最大值：max_element(a.begin(), a.end())**


---
	class Solution {
	public:
	    int rob(vector<int>& nums) {
	        if(nums.size() == 0) return 0;
	        if(nums.size() == 1) return nums[0];
	        vector<int> g;
	        g.push_back(nums[0]);
	        g.push_back(max(nums[0], nums[1]));
	        for(int i = 2; i < nums.size(); i++) g.push_back(max(g[i - 1],  g[i - 2] + nums[i]));
	        return *max_element(g.begin(), g.end());
	    }
	};
---