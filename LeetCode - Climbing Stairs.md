### LeetCode - Climbing Stairs

原题网址：
https://leetcode.com/problems/climbing-stairs/#/description

You are climbing a stair case. It takes *n* steps to reach to the top.
Each time you can either climb 1 or 2 steps. In how many distinct ways can you climb to the top?
**Note:** Given *n* will be a positive integer.

题解：

　　爬楼梯问题，每次可爬一阶楼梯或者两阶，爬到顶部时共有几种方式。

- 爬一阶楼梯，一种方式，记作$f(1)=1$
- 爬两阶楼梯，两种方式，记作$f(2)=2$
- 爬三阶楼梯，$f(3)=3=f(2)+f(1)$
- 爬 i 阶楼梯，$f(i)=f(i-2)+f(i-1)$

　　直观的看一下上述的递归情况：

![LeetCode - Climbing Stairs](D:\SuperMary\Documents\Markdown\pic\LeetCode - Climbing Stairs.png)

　　这是一个三阶台阶，第一步有两种选择，当第一步走一个台阶，则一共的可能性与爬两节台阶时一样；当第一步走两个台阶时，则一共的可能性与爬一阶台阶时一样。因此有$f(3)=f(2)+f(1)$。我们发现这实质上是一组斐波那契数列。

　　很明显这是一个动态规划问题，动态规划有两种方法，自顶向下的递归方法与自底向上的递推法。这道题我们就用递推法，一次计算台阶为$3、4、...​$时的方法总数，并记录到数组中。

附上代码：

```c++
class Solution {
public:
    int climbStairs(int n) {
        vector<int> solution(n);
    	solution[0] = 1;
    	solution[1] = 2;
    	for(int i=2;i<=n-1;i++)
    	{
    		solution[i] = solution[i-1] + solution[i-2];
    	}
    	return solution[n-1];
        
    }
};
```