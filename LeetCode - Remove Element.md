### LeetCode - Remove Element

原题网址：https://leetcode.com/problems/remove-element/#/description

Given an array and a value, remove all instances of that value in place and return the new length. Do not allocate extra space for another array, you must do this in place with constant memory. The order of elements can be changed. It doesn't matter what you leave beyond the new length.

**Example:**
Given input array *nums* = `[3,2,2,3]`, *val* = `3`. Your function should return length = 2, with the first two elements of *nums* being 2.

题解：
  遍历数组，当nums[i] = val时，删除这个数，最后返回数组长度即可。删除和返回数组长度都可以直接用vector中的函数。
  
非常简单，所以直接给出代码：

```c++
class Solution {
public:
    int removeElement(vector<int>& nums, int val) 
    {
        for(int i=0;i<nums.size();i++)
        {
        	if(nums[i] == val)
        	{
        		nums.erase(nums.begin()+i);
        		i -= 1;
        	}
        }
        return nums.size();
    }
};
```