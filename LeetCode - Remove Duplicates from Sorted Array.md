### LeetCode - Remove Duplicates from Sorted Array



原题网址：https://leetcode.com/problems/remove-duplicates-from-sorted-array/#/description

Given a sorted array, remove the duplicates in place such that each element appear only *once* and return the new length. Do not allocate extra space for another array, you must do this in place with constant memory.   							

For example,
Given input array *nums* = `[1,1,2]`, Your function should return length = `2`, with the first two elements of *nums* being `1` and `2` respectively. It doesn't matter what you leave beyond the new length.

题解：

   遍历数组 nums，当nums[i+1]=nums[i]时，删除第i个数组，此时数组长度减1，继续比较第i+1个数与第i个数（而不是比较第i+2与第i+1个数），直到比较到最后一个数，返回数组长度（同时可以返回去重后的数组）。



代码如下：

```c++
class Solution {
public:
    int removeDuplicates(vector<int>& nums) 
    {
        if(nums.empty()) return 0;
        int i = 0;
        while(nums[i]!=nums.back())
        {
        if (nums[i+1]==nums[i]) 
        {
            nums.erase(nums.begin()+i);
            i -= 1;
        }
        i += 1;
        }
        nums.erase(nums.begin()+i+1,nums.end());
        return nums.size();
    }
};
```


转载请附上本文网址：