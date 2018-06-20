# LeetCode283.移动零
## 题目
给定一个数组 nums，编写一个函数将所有 0 移动到数组的末尾，同时保持非零元素的相对顺序。

## eg1
输入: [0,1,0,3,12]

输出: [1,3,12,0,0]

## 说明
1. 必须在原数组上操作，不能拷贝额外的数组。
2. 尽量减少操作次数。



## 默认代码模板

	class Solution {
	public:
	    void moveZeroes(vector<int>& nums) {
	        
	    }
	};


## 解法1
旋转数组的应用

声明两个迭代器一前(nums.begin())一后(nums.end())

当前面的迭代器发现0时，就把前迭代器后一元素至后迭代器中间的元素向前移动一位，然后吧后迭代器赋值为0

重复操作，直至前后迭代器相同为止

---

	class Solution {
	public:
	    void moveZeroes(vector<int>& nums) {
	        vector<int>::iterator it = nums.begin();
	        vector<int>::iterator it_0 = nums.end() - 1;
	        for(; it != it_0;)
	        {
	            if(*it == 0)
	            {
	                vector<int>::iterator temp = (it + 1);
	                for(; temp != it_0 + 1; temp++)
	                {
	                    *(temp - 1) = *temp;
	                }
	                *(temp - 1) = 0;
	                it_0--;
	            }
	            else it++;
	        }
	    }
	};

---

## 解法2

与解法1思路完全相同

只是用数组下标操作

比解法1快一些

---

	class Solution {
	public:
	    void moveZeroes(vector<int>& nums) {
	        int i = 0;
	        int j = nums.size() - 1;
	        for(; i != j;)
	        {
	            if(nums[i] == 0)
	            {
	                int temp = i + 1;
	                for(; temp != j + 1; temp++)
	                {
	                    nums[temp - 1] = nums[temp];
	                }
	                nums[temp - 1] = 0;
	                j--;
	            }
	            else i++;
	        }
	    }
	};

---