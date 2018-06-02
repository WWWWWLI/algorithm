# LeetCode350.两个数组的交集 II
## 题目
给定两个数组，写一个方法来计算它们的交集。

## eg1
给定 nums1 = [1, 2, 2, 1], nums2 = [2, 2], 返回 [2, 2].

## 注意

- 输出结果中每个元素出现的次数，应与元素在两个数组中出现的次数一致。
- 我们可以不考虑输出结果的顺序。

## 跟进

- 如果给定的数组已经排好序呢？你将如何优化你的算法？
- 如果 nums1 的大小比 nums2 小很多，哪种方法更优？
- 如果nums2的元素存储在磁盘上，内存是有限的，你不能一次加载所有的元素到内存中，你该怎么办？


## 默认代码模板

	class Solution {
	public:
	    vector<int> intersect(vector<int>& nums1, vector<int>& nums2) {
	        
	    }
	};


## 解法

声明两个迭代器it1与it2，分别用于遍历nums1与nums2

声明一个目标数组vec

如果\*it1 = \*it2，则向vec插入\*it1

如果不等，哪个值小就++哪个

---

	class Solution {
	public:
	    vector<int> intersect(vector<int>& nums1, vector<int>& nums2) {
	        vector<int> vec;
	        vector<int>::iterator it1 = nums1.begin();
	        vector<int>::iterator it2 = nums2.begin();
	        sort(nums1.begin(),nums1.end());
	        sort(nums2.begin(),nums2.end());
	        for(; it1 != nums1.end() && it2 != nums2.end();)
	        {
	            if(*it1 < *it2) it1++;
	            else if(*it1 == *it2) 
	            {
	                vec.push_back(*it1);
	                it1++;
	                it2++;
	            }
	            else it2++;
	        }
	        return vec;
	    }
	};

---
