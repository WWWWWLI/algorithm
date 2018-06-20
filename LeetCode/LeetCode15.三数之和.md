# LeetCode15.三数之和
## 题目
给定一个包含 n 个整数的数组 nums，判断 nums 中是否存在三个元素 a，b，c ，使得 a + b + c = 0 ？找出所有满足条件且不重复的三元组。

**注意：**答案中不可以包含重复的三元组。
## eg1
例如, 给定数组 nums = [-1, 0, 1, 2, -1, -4]，

满足要求的三元组集合为：
[
  [-1, 0, 1],
  [-1, -1, 2]
]

## 默认代码模板

	class Solution {
	public:
	    vector<vector<int>> threeSum(vector<int>& nums) {
	        
	    }
	};


## 解法1
三重循环判断是否和为0

当找到和为0的三个值后，判断是否重复

判断重复的方法是通过遍历符合条件的二维向量

**此方法经运行后不符合时间要求 时间复杂度过高**

---

	class Solution {
	public:
		vector<vector<int>> threeSum(vector<int>& nums) {
			vector<vector<int>> vecvec;
	        if(nums.size() < 3) return vecvec;
			for (int i = 0; i < nums.size() - 2; i++)
			{
				for (int j = i + 1; j < nums.size() - 1; j++)
				{
					for (int k = j + 1; k < nums.size(); k++)
					{
						if (nums[i] + nums[j] + nums[k] == 0)
						{
							vector<int> vec;
							vec.push_back(nums[i]);
							vec.push_back(nums[j]);
							vec.push_back(nums[k]);
							sort(vec.begin(), vec.end());
							if(vecvec.size() == 0) vecvec.push_back(vec);
							else
							{
								for (int m = 0; m < vecvec.size(); m++)
								{
									if (vecvec[m][0] == vec[0] && vecvec[m][1] == vec[1]) break;
									if (m == vecvec.size() - 1) vecvec.push_back(vec);
								}
							}
						}
					}
				}
			}
			return vecvec;
		}
	};



---

## 解法2

数组从小到大排序

三个迭代器按照num1 target num2的顺序

num1,num2不能越过target

目标是找num1 + num2 = -target

当num1 + num2 < -target时 num1++

当num1 + num2 > -target时 num2--

**本题的难点在于避免重复**

非正常情况下（三个数字存在重复）

定义flag [-2 -1 -1 0 1 2]

flag = 0 代表target是第一个-1

flag = 1 代表target是第二个-1

每次迭代初始化时，flag = 0 num1 = nums.begin(), flag = 1 num2 = target - 1

---

	class Solution {
	public:
		vector<vector<int>> threeSum(vector<int>& nums) {
			sort(nums.begin(), nums.end());
			vector<vector<int> > vecvec;
			if (nums.size() < 3) return vecvec;
			vector<int>::iterator num1;
			vector<int>::iterator num2;
			vector<int>::iterator target = nums.begin() + 1;
			int flag;
			if (*target == *(target - 1)) flag = 1;
			else flag = 0;
			for (; target != nums.end() - 1;)
			{
				if (flag == 0)
				{
					num1 = nums.begin();
				}
				else
				{
					num1 = target - 1;
				}
				
				num2 = nums.end() - 1;
				while (num1 != target && num2 != target)
				{
					if (*num1 + *num2 > -*target) num2--;
					else if (*num1 + *num2 < -*target) num1++;
					else
					{
						vector<int> vec;
						vec.push_back(*num1);
						vec.push_back(*target);
						vec.push_back(*num2);
						vecvec.push_back(vec);
						while (*num1 == *(num1 + 1) && num1 != target)
						{
							num1++;
						}
						if (num1 == target) break;
						else num1++;
						if (num1 == target) break;
						while (*num2 == *(num2 - 1) && num2 != target)
						{
							num2--;
						}
						if (num2 == target) break;
						else num2--;
						if (num2 == target) break;
					}
				}
				if (*target != *(target + 1))
				{
					target++;
					flag = 0;
				}
				else if (flag == 0 && *target == *(target + 1))
				{
					target++;
					flag++;
				}
				else if (flag == 1 && *target == *(target + 1))
				{
					while (target != nums.end() - 1 && *target == *(target + 1)) target++;
					if (target != nums.end() - 1)
					{
						target++;
						flag = 0;
					}
				}
			}
			return vecvec;
		}
	};

---
