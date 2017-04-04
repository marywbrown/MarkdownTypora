### LeetCode - Length of Last Word



原题网址：https://leetcode.com/problems/length-of-last-word/#/description

Given a string *s* consists of upper/lower-case alphabets and empty space characters `' '`, return the length of last word in the string.If the last word does not exist, return 0.

**Note:** A word is defined as a character sequence consists of non-space characters only.

  For example, 
Given *s* = `"Hello World"`,
return `5`.



题解：　　

　　返回一句话最后一个单词的字母数，按空格分割单词。一个最简单的想法就是，从字符串的最后一位倒着向前取，遇到空格停止，每向前扫描一位则计数加一，但是要考虑下面三种情况：

- "  Hello   "   -  最后有多个空格
- "" - 没有任何输入
- "Hello" - 只有一个单词，并且前面没有空格

　　因此我们从字符串的最后向前扫描，如果字符串长度为0，输出0；如果字符串末尾是空格，向前扫描并不计数，直到扫描到非空格字符开始计数，同时判断该字符是不是首位字符或者空格字符，若是首位字符或者空格字符则停止扫描，输出最终计数。

```c++
class Solution {
public:
    int lengthOfLastWord(string s) {
        int len = s.length();
        int count = 0;
        if(s=="") return 0;
        while(s[len-1]==' ')
        {
        	len -= 1;
        	if(len==0) return 0;
        }
        while(len!=0)
        {   
        	if(s[len-1]==' ') break;
        	len -= 1;
        	count+=1;
        } 
        return count;
    }
};
```