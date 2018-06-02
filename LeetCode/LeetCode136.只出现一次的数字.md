# LeetCode136.只出现一次的数字
## 题目
给定一个非空整数数组，除了某个元素只出现一次以外，其余每个元素均出现两次。找出那个只出现了一次的元素。

说明：

你的算法应该具有线性时间复杂度。 你可以不使用额外空间来实现吗？

## eg1
输入: [2,2,1]

输出: 1

## eg2
输入: [4,1,2,1,2]

输出: 4

## 默认代码模板

	int singleNumber(vector<int>& nums) {
		public:
    	bool containsDuplicate(vector<int>& nums) {
        
    	}
	};


## 解法1

题目中明确为非空数组，所以可以不用进行判空操作

先将数组排序，保证相同元素相邻

声明迭代器it 每次判断\*it 与 \*(it + 1)是否相等

如果相等则it指向后面第二个（跳过一个）

如果不相等的话，*it就指向的是只出现一次的数字

---

	class Solution {
	public:
	    int singleNumber(vector<int>& nums) {
	        vector<int>::iterator it = nums.begin();
	        sort(nums.begin(),nums.end());
	        for(;(it + 1) != nums.end();)
	        {
	            if(*it == *(it + 1)) it = it + 2;
	            else break;
	        }
	        return *it;
	    }
	};

---

## 解法2
思路同解法1

**注意：由于返回值需要包含i的位置，所以声明i必须要在for循环之外**
**如果写for(int i = 0; i < nums.size() - 1;)的话，则报错**

---

	class Solution {
	public:
	    int singleNumber(vector<int>& nums) {
	        sort(nums.begin(),nums.end());
	        int i = 0;
	        for(; i < nums.size() - 1;)
	        {
	            if(nums[i] == nums[i + 1]) i += 2;
	            else break;
	        }
	        return nums[i];
	    }
	};

---