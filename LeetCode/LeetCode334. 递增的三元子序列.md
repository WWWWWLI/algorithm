# 334. 递增的三元子序列
## 题目
给定一个未排序的数组，请判断这个数组中是否存在长度为3的递增的子序列。

正式的数学表达如下:

	如果存在这样的 i, j, k,  且满足 0 ≤ i < j < k ≤ n-1，
	使得 arr[i] < arr[j] < arr[k] ，返回 true ; 否则返回 false 。

说明: 要求算法时间复杂度为O(n)，空间复杂度为O(1) 。

## eg1

输入: [1,2,3,4,5]
输出: true

## eg2

输入: [5,4,3,2,1]
输出: false

## 默认代码模板

	class Solution {
		public:
    	bool increasingTriplet(vector<int>& nums) {
        
    	}
	};


## 解法

设置两个变量num1，num2，初始设为最大值。遍历数组，如果有比num1小的，就把num1换成那个元素，如果有比num1大且比num2小的，把num2换掉，这两步其实是在模拟第300题中元素的替换。最后，当存在比num1和num2都大的数，那么就可以直接返回true了

---

	class Solution {
	public:
	    bool increasingTriplet(vector<int>& nums) {
	        if(nums.size() <= 2) return false;
	        int small = *max_element(nums.begin(), nums.end());
	        int mid = *max_element(nums.begin(), nums.end());
	        for(int i = 0; i < nums.size(); i++){
	            if(nums[i] < small) small = nums[i];
	            if(nums[i] > small && nums[i] < mid) mid = nums[i];
	            if(nums[i] > small && nums[i] > mid) return true;
	        }
	        return false;
	    }
	};

---

