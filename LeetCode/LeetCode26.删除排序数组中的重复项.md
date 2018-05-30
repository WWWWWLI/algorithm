# LeetCode26.删除排序数组中的重复项
## 题目
给定一个排序数组，你需要在原地删除重复出现的元素，使得每个元素只出现一次，返回移除后数组的新长度。

不要使用额外的数组空间，你必须在原地修改输入数组并在使用 O(1) 额外空间的条件下完成。

## eg1
给定数组 nums = [1,1,2], 

函数应该返回新的长度 2, 并且原数组 nums 的前两个元素被修改为 1, 2。 

你不需要考虑数组中超出新长度后面的元素。

## eg2
给定 nums = [0,0,1,1,1,2,2,3,3,4],

函数应该返回新的长度 5, 并且原数组 nums 的前五个元素被修改为 0, 1, 2, 3, 4。

你不需要考虑数组中超出新长度后面的元素。

## 默认代码模板

	class Solution {
		public:
    	int removeDuplicates(vector<int>& nums) {
        
    	}
	};

## 注意
数组中的数据是排列好的，即相同元素在临近位置不会出现[1,1,2,2,1]类似的情况

## 解法一

第一次没有审好题，以为必须要把数组删除至唯一数组的长度

所以利用了vector的erase()方法

声明两个迭代器it1 it2，it2指向it1后一个元素

当it1与it2值相同时，删除it1指向元素，将it1和it2后移

当it1与it2不同时，仅将it1与it2后移

**但是，声明迭代器后，如果对向量进行删除或插入操作，则迭代器失效**

**所以每次erase()后，必须进行迭代器的重新声明**

**在本例中it1,it2每次必须重新赋值**

**可以利用it = vec.erase(it)使it指向删除后的下一个元素**

**在进行单个元素删除后，传入的迭代器指向不变，仍然指向被删除元素的位置，而被删除元素之后的所有元素都向前移动一位，也就是该迭代器实际上是指向了原来被删除元素的下一个元素**

---
	class Solution {
	public:
		int removeDuplicates(vector<int>& nums) {
			if (nums.size() == 0) return 0;
			if (nums.size() == 1) return 1;
			vector<int>::iterator it1 = nums.begin();
			vector<int>::iterator it2 = nums.begin();
			it2++;
			for (; it2 != nums.end();)
			{
				if (*it1 == *it2)
				{
	
					it1 = nums.erase(it1);
					it1 = nums.begin();
					it2 = it1 + 1;
				}
				else
				{
					++it1;
					++it2;
				}
				
			}
	
			return nums.size();
		}
	};

---

## 解法2
其实本题可以利用一个迭代器it1就可完成，每次判断\*it1是否与\*(it1+1)相等

如果相等，删除it1 = vec.erase(it1)删除当前it1指向，并使it1指向下一个

如果不等的话直接++it1

**由于利用了\*(it1 + 1)所以需要判断it1+1是否为vec.end()**

**如果是end的话，就说明已经结束了**

---
	class Solution {
	public:
		int removeDuplicates(vector<int>& nums) {
			if (nums.size() == 0) return 0;
			if (nums.size() == 1) return 1;
			vector<int>::iterator it1 = nums.begin();
			for (; it1 != nums.end();)
			{
				if ((it1 + 1) != nums.end() && *it1 == *(it1 + 1))
				{
	
					it1 = nums.erase(it1);
				}
				else
				{
					++it1;
				}
			}
			return nums.size();
		}
	};

---

## 解法3
其实本题不用将数组长度改变，只需将数组前面的元素改成唯一出现的元素即可

这样的话就不需要每次修改数组时，初始化迭代器了
