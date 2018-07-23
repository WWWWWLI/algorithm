# 155. 最小栈
## 题目
设计一个支持 push，pop，top 操作，并能在常数时间内检索到最小元素的栈。
- push(x) -- 将元素 x 推入栈中。
- pop() -- 删除栈顶的元素。
- top() -- 获取栈顶元素。
- getMin() -- 检索栈中的最小元素。


## eg
MinStack minStack = new MinStack();
minStack.push(-2);
minStack.push(0);
minStack.push(-3);
minStack.getMin();   --> 返回 -3.
minStack.pop();
minStack.top();      --> 返回 0.
minStack.getMin();   --> 返回 -2.

## 默认代码模板
	class MinStack {
	public:
	    /** initialize your data structure here. */
	    MinStack() {
	        
	    }
	    
	    void push(int x) {
	        
	    }
	    
	    void pop() {
	        
	    }
	    
	    int top() {
	        
	    }
	    
	    int getMin() {
	        
	    }
	};

/**
 * Your MinStack object will be instantiated and called as such:
 * MinStack obj = new MinStack();
 * obj.push(x);
 * obj.pop();
 * int param_3 = obj.top();
 * int param_4 = obj.getMin();
 */

## 正确解法
- 设计两个栈
- 第一个s用来记录数据
- 第二个s_min用来记录对应数据为栈顶时栈的最大值
- 当来一个新数据的时候，先入栈s,然后判断新数据与s_min栈顶元素的大小
- 如果新数据大于等于s_min栈顶元素，说明加入新数据后，栈s的最小值仍然为s_min栈顶元素值，将s_min栈顶元素再次入栈
- 如果新数据小于s_min栈顶元素，说明加入新数据后，栈s的最小值为新数据值，将新数据入栈s_min


---
	class MinStack {
	public:
	    /** initialize your data structure here. */
	    MinStack() {
	        
	    }
	    
	    void push(int x) {
	        s.push(x);
	        if(s_min.empty() || x < s_min.top()) s_min.push(x);
	        else s_min.push(s_min.top());
	    }
	    
	    void pop() {
	        s.pop();
	        s_min.pop();
	    }
	    
	    int top() {
	        return s.top();
	    }
	    
	    int getMin() {
	        return s_min.top();
	    }
	    
	private:
	    stack<int> s;
	    stack<int> s_min;
	    
	};
	
	/**
	 * Your MinStack object will be instantiated and called as such:
	 * MinStack obj = new MinStack();
	 * obj.push(x);
	 * obj.pop();
	 * int param_3 = obj.top();
	 * int param_4 = obj.getMin();
	 */
---