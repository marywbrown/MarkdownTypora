### LeetCode - Plus One



原题网址：https://leetcode.com/problems/plus-one/#/description

Given a non-negative integer represented as a **non-empty** array of digits, plus one to the integer. You may assume the integer do not contain any leading zero, except the number 0 itself. The digits are stored such that the most significant digit is at the head of the list.

题解：

　　用一个数组来表示一个10进制的非负整数，数组的首位存放整数的最高位，末位存放整数的个位数。现在要求给这个数加一后仍存放在数组中显示。

　　我们只需要判断数组末位数是否为9，若为9则变为0，向数组前一位扫描，若为9依然变为0，直到某一位不为9时，这一位数加1，然后输出该数组。若扫描结束后，发现最高位为0，则全部进位，在数组首位插入一个1，输出该数组。

附上代码：

```c++
class Solution {
public:
    vector<int> plusOne(vector<int>& digits) {
    	for(int i = digits.size() - 1; i >= 0; i--)
    	{
    		if (digits[i] == 9)
    		{
    			digits[i] = 0;
    		}
    		else
    		{
    		    digits[i] = digits[i] + 1;
    		    break;
    		}
    	}
    	if (digits[0] == 0) digits.insert(digits.begin(),1);
        return digits;
    }
};
```

转载请附上本文链接：