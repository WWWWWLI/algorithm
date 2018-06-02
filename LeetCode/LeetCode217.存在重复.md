# LeetCode217.存在重复
## 题目
给定一个整数数组，判断是否存在重复元素。

如果任何值在数组中出现至少两次，函数返回 true。如果数组中每个元素都不相同，则返回 false。

## eg1
输入: [1,2,3,1]

输出: true

## eg2
输入: [1,2,3,4]

输出: false

## eg3
输入: [1,1,1,3,3,4,3,2,4,2]

输出: true

## 默认代码模板

	class Solution {
		public:
    	bool containsDuplicate(vector<int>& nums) {
        
    	}
	};


## 解法

当输入数组长度为0或1时，肯定没有重复，所以返回false

当输入数组长度大于等于2时，先将数组排序，然后反复检查前一个和后一个是否相等，如果相等说明存在重复，返回true；如果遍历结束都不相等，说明不存在重复，返回false

---

	class Solution {
	public:
	    bool containsDuplicate(vector<int>& nums) {
	        if(nums.size() <= 1) return false;
	        sort(nums.begin(), nums.end());
	        vector<int>::iterator it = nums.begin();
	        for(; (it + 1) != nums.end(); it++)
	        {
	            if(*it == *(it + 1)) break;
	        }
	        if((it + 1) != nums.end()) return true;
	        
	        return false;
	    }
	};

---
