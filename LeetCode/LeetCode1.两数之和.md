# LeetCode1.两数之和
## 题目
给定一个整数数组和一个目标值，找出数组中和为目标值的两个数。

你可以假设每个输入只对应一种答案，且同样的元素不能被重复利用。

## eg1
给定 nums = [2, 7, 11, 15], target = 9

因为 nums[0] + nums[1] = 2 + 7 = 9

所以返回 [0, 1]

## 默认代码模板

	class Solution {
	public:
	    vector<int> twoSum(vector<int>& nums, int target) {
	        
	    }
	};


## 解法1

二重循环遍历数组，直到找到和为target

**注意：同一个数组不能相加**



---

	class Solution {
	public:
	    vector<int> twoSum(vector<int>& nums, int target) {
	        int a[2];
	        for(int i = 0;i < nums.size(); i++)
	        {
	            for(int j = 0; j < i; j++)
	            {
	                if(nums[i] + nums[j] == target)
	                {
	                    a[0] = i;
	                    a[1] = j;
	                    break;
	                }
	            }
	            for(int j = i + 1; j < nums.size(); j++)
	            {
	                if(nums[i] + nums[j] == target)
	                {
	                    a[0] = i;
	                    a[1] = j;
	                    break;
	                }
	            }
	        }
	        vector<int> b(a, a + 2);
	        return b;
	    }
	};



---
