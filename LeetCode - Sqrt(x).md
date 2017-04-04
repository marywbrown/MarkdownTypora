### LeetCode - Sqrt(x)

原题网址：
https://leetcode.com/problems/sqrtx/#/description

Implement `int sqrt(int x)`. Compute and return the square root of *x*.

题解：

　　求正整数$x$的开方，即找到 $y$  使得 $y^2<=x<(y+1)^2$ 。

　　最简单的想法就是使 $y$ 从零开始计算，逐次加1，直到满足要求为止，但是这样需要的时间非常久，在LeetCode中会报错超出时间。

​	这里我们用一个最优化的方法——牛顿法。

　　牛顿法首先将非线性函数$f(x)$在$x_0$处展开泰勒级数，并取线性部分，得到一个近似的线性函数。
$$
f(x)=f(x_0)+\frac{f'(x_0)}{1!}(x-x_0)+\frac{f''(x_0)}{2!}(x-x_0)^2+...
$$
　　取线性部分得到：
$$
f(x)=f(x_0)+f'(x_0)(x-x_0)
$$

$$
x=x_0-\frac{f(x_0)}{f'(x_0)}
$$

　　$x_0$ 是一个初始的自己设置的值，通过一次计算我们可以得到一个近似解$x$，但这个解并不是真实的解。我们令 $x_0=x$ 二次计算来得到新的解 $x$，通过不断地迭代来逼近真实值。直到两次两次得到解小于一个阈值，停止迭代。

　　下面这个图取自wiki，非常直观的展示了牛顿法迭代逼近最优解的过程：

![NewtonIteration_Ani](pic/NewtonIteration_Ani.gif)

　　在这道题中我们构造的函数 $f(x)=y^2-x=0$，带入公式（3）得：
$$
y =\frac{y_0^2+x}{2y_0}
$$
 　　设初始的 $y_0=1$。

附上代码：

```c++
class Solution {
public:
    int mySqrt(int x) {
    	if (x==0) return 0;
    	float y = 1, y1;
    	int output;
    	while(1)
    	{
    		y1 = (x + y*y) / (2*y);
    		if(abs(y1-y) < 0.1) break;
    		y = y1;
    	}
    	output = int(y);
    	while(output*output > x)
        {
            output -= 1;
        }
        return output;
    }
};
```

转载请附上本文链接：

