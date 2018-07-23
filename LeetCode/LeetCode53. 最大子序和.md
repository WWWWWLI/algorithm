# 53. 最大子序和
## 题目
给定一个整数数组 nums ，找到一个具有最大和的连续子数组（子数组最少包含一个元素），返回其最大和。

## eg1
输入: [-2,1,-3,4,-1,2,1,-5,4],
输出: 6
解释: 连续子数组 [4,-1,2,1] 的和最大，为 6。

## 默认代码模板
	class Solution {
	public:
	    int maxSubArray(vector<int>& nums) {
	        
	    }
	};

## 正确解法
- 定义两个变量res和curSum，其中res保存最终要返回的结果，即最大的子数组之和
- curSum初始值为0，每遍历一个数字num，比较curSum + num和num中的较大值存入curSum，然后再把res和curSum中的较大值存入res
- 以此类推直到遍历完整个数组，可得到最大子数组的值存在res中。


---
	class Solution {
	public:
	    int maxSubArray(vector<int>& nums) {
	        int res = nums[0];//保存全局最大值，即要返回的值
	        int cursum = nums[0];
	        for(int i = 1; i < nums.size(); i++)
	        {
	            if(cursum + nums[i] > nums[i]) cursum += nums[i];
	            else cursum = nums[i];
	            if(cursum > res) res = cursum;
	        }
	        return res;
	    }
	};
---