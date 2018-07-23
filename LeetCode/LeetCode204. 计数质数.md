# 204. 计数质数
## 题目
统计所有小于非负整数 n 的质数的数量。

## eg1
输入: 10
输出: 4
解释: 小于 10 的质数一共有 4 个, 它们是 2, 3, 5, 7 。
## 默认代码模板
	class Solution {
	public:
	    int countPrimes(int n) {
	        
	    }
	};

## 正确解法
- 这道题给定一个非负数n，让我们求小于n的质数的个数，题目中给了充足的提示，解题方法就在第二个提示埃拉托斯特尼筛法Sieve of Eratosthenes中，这个算法的过程如下图所示，我们从2开始遍历到根号n，先找到第一个质数2，然后将其所有的倍数全部标记出来，然后到下一个质数3，标记其所有倍数，一次类推，直到根号n，此时数组中未被标记的数字就是质数。我们需要一个n-1长度的bool型数组来记录每个数字是否被标记，长度为n-1的原因是题目说是小于n的质数个数，并不包括n。 然后我们用两个for循环来实现埃拉托斯特尼筛法，难度并不是很大，代码如下所示：

![](https://i.imgur.com/O7hHyBY.gif)

---
	class Solution {
	public:
	    int countPrimes(int n) {
	        if(n <= 1) return 0;
	        int count = 0;
	        int flags[n] = {0};
	        for(int i = 2; i <= sqrt(n) + 1; i++)
	        {
	            if(isPrimes(i))
	            {
	                int k = 2;
	                while(i * k < n)
	                {
	                    flags[i * k] = 1;
	                    k++;
	                }
	            }
	        }
	        for(int i = 2; i < n; i++) if(flags[i] == 0) count++;
	        return count;
	    }
	    
	    bool isPrimes(int n)
	    {
	        for(int i = 2; i <= n - 1; i++)
	        {
	            if(n % i == 0) return false; 
	        }
	        return true;
	    }
	};
---