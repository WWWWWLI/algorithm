# 73. 矩阵置零
## 题目
给定一个 m x n 的矩阵，如果一个元素为 0，则将其所在行和列的所有元素都设为 0。请使用原地算法。

## eg1

	输入: 
	[
	  [1,1,1],
	  [1,0,1],
	  [1,1,1]
	]
	输出: 
	[
	  [1,0,1],
	  [0,0,0],
	  [1,0,1]
	]

## eg2

	输入: 
	[
	  [0,1,2,0],
	  [3,4,5,2],
	  [1,3,1,5]
	]
	输出: 
	[
	  [0,0,0,0],
	  [0,4,5,0],
	  [0,3,1,0]
	]

## 默认代码模板

	class Solution {
		public:
    	void setZeroes(vector<vector<int>>& matrix) {
        
    	}
	};

## 解法一

赋值另存一个m*n的矩阵，在原矩阵为零的值相应置新的矩阵行和列为零。额外空间为O(m*n).

---

	class Solution {
	public:
	    void setZeroes(vector<vector<int>>& matrix) {
	        vector<vector<int> > mat = matrix;
	        int m = matrix.size();
	        int n = matrix[0].size();
	        for(int i = 0; i < m; i++)
	        {
	            for(int j = 0; j < n; j++)
	            {
	                if(mat[i][j] == 0)
	                {
	                    for(int a = 0; a < n; a++) matrix[i][a] = 0;
	                    for(int a = 0; a < m; a++) matrix[a][j] = 0;
	                }
	            }
	        }
	    }
	};

---


