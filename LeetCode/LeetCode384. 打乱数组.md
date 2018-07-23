# 384. 打乱数组
## 题目
打乱一个没有重复元素的数组。

## eg1
// 以数字集合 1, 2 和 3 初始化数组。
int[] nums = {1,2,3};
Solution solution = new Solution(nums);

// 打乱数组 [1,2,3] 并返回结果。任何 [1,2,3]的排列返回的概率应该相同。
solution.shuffle();

// 重设数组到它的初始状态[1,2,3]。
solution.reset();

// 随机返回数组[1,2,3]打乱后的结果。
solution.shuffle();
## 默认代码模板
	class Solution {
	public:
	    Solution(vector<int> nums) {
	        
	    }
	    
	    /** Resets the array to its original configuration and return it. */
	    vector<int> reset() {
	        
	    }
	    
	    /** Returns a random shuffling of the array. */
	    vector<int> shuffle() {
	        
	    }
	};

	/**
	 * Your Solution object will be instantiated and called as such:
	 * Solution obj = new Solution(nums);
	 * vector<int> param_1 = obj.reset();
	 * vector<int> param_2 = obj.shuffle();
	 */

## 正确解法
- 问题的本质是从n!种（n为数组长度）排列组合中等概率选取一种
- 倒序遍历，将当前元素i与[0,i]个元素其中之一进行交换
- 倒序是为了方便获取下标
- swap函数c++自带直接使用


---
	class Solution {
	public:
	    vector<int> vec;
	    vector<int> nums_copy;
	    Solution(vector<int> nums) {
	        nums_copy = nums;
	        vec = nums;
	    }
	    
	    /** Resets the array to its original configuration and return it. */
	    vector<int> reset() {
	        vec = nums_copy;
	        return vec;
	    }
	    
	    /** Returns a random shuffling of the array. */
	    vector<int> shuffle() {
	        for(int i = vec.size() - 1; i >= 0; i--)
	        {
	            swap(vec[i], vec[rand() % (i + 1)]); 
	        }
	        return vec;
	    }
	};
	
	/**
	 * Your Solution object will be instantiated and called as such:
	 * Solution obj = new Solution(nums);
	 * vector<int> param_1 = obj.reset();
	 * vector<int> param_2 = obj.shuffle();
	 */
---