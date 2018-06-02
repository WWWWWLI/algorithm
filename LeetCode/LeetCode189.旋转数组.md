# LeetCode189.旋转数组
## 题目
给定一个数组，将数组中的元素向右移动 k 个位置，其中 k 是非负数。

## eg1
输入: [1,2,3,4,5,6,7] 和 k = 3

输出: [5,6,7,1,2,3,4]

解释:

向右旋转 1 步: [7,1,2,3,4,5,6]

向右旋转 2 步: [6,7,1,2,3,4,5]

向右旋转 3 步: [5,6,7,1,2,3,4]

## eg2
输入: [-1,-100,3,99] 和 k = 2

输出: [3,99,-1,-100]

解释: 

向右旋转 1 步: [99,-1,-100,3]

向右旋转 2 步: [3,99,-1,-100]



## 默认代码模板

	class Solution {
		public:
    	void rotate(vector<int>& nums, int k) {
        
    	}
	};


## 解法1

可以将旋转的步骤分解，就如例子一样，每次将最后一个值放在第一位，然后把之前的元素都后移一位

---

	class Solution {
	public:
	    void rotate(vector<int>& nums, int k) {
	        k = k % nums.size();
	        int temp;
	        for(int i = 0; i < k; i++)
	        {
	            temp = nums[nums.size() - 1];//取最后一个元素
	            for(int j = nums.size() - 1;j > 0; j--)
	            {
	                nums[j] = nums[j - 1];
	            }
	            nums[0] = temp;
	        }
	    }
	};

---
