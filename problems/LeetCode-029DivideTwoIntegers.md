---
title: LeetCode刷题笔记-029DivideTwoIntegers
date: 2018-05-03 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

给定两个整数，被除数 dividend 和除数 divisor。将两数相除，要求不使用乘法、除法和 mod 运算符。
返回被除数 dividend 除以除数 divisor 得到的商。
示例 1:
输入: dividend = 10, divisor = 3
输出: 3
示例 2:
输入: dividend = 7, divisor = -3
输出: -2
说明:
被除数和除数均为 32 位有符号整数。
除数不为 0。
假设我们的环境只能存储 32 位有符号整数，其数值范围是 [−2^31,  2^31 − 1]。本题中，如果除法结果溢出，则返回 2^31 − 1。

**分析**

将除法转换为减法，比如8除以2等同于8-2-2-2-2；但直接除的话一定会超时，
所以可以把减法转换为位移运算，比如29除以8等同于29-8\*2^1-8\*2^0-5，结果商为2^1+2^0即3
这题我用java死活通不过，使用网上别的写的C语言版本就可以，不知道翻译的哪里错了。
不过题目解法的思想是懂了，也算有所收获吧_(:з」∠)_

**解答：**

````java
package net.jerryfu.leetCodeMedium;

import static org.junit.Assert.assertEquals;
import org.junit.Test;
public class _024SwapNodesInPairs {

	 public class _029DivideTwoIntegers {

	public int divide(int dividend, int divisor) {
		if (divisor == 0 || (dividend == Integer.MIN_VALUE && divisor == -1)) {
			return Integer.MAX_VALUE;
		}
		if (divisor==1) {
			return dividend;
		}
		int dd = Math.abs(dividend);
		int ds = Math.abs(divisor);
		int sign = ((dividend < 0) ^ (divisor < 0)) ? -1 : 1;
		int result = 0;
		while (dd >= ds) {
			int temp = ds, times = 1;
			while (dd > (temp << 1)) {
				times <<= 1;
				temp <<= 1;
			}
			result += times;
			dd -= temp;
		}
		return sign > 0 ? result : -result;
	}

	@Test
	public void test() {
		assertEquals(3, divide(10, 3));
		assertEquals(3, divide(29, 8));
		assertEquals(-2, divide(7, -3));
		assertEquals(4, divide(8, 2));
		assertEquals(0, divide(2, 8));
		assertEquals(1, divide(2, 2));
		assertEquals(2147483647, divide(2147483647, 1));
	}
}

````

附上可以通过的C++版本

````c++
class Solution {
public:
    int divide(int dividend, int divisor) {
        long long m = abs((long long)dividend), n = abs((long long)divisor), res = 0;
        if (m < n) return 0;    
        while (m >= n) {
            long long t = n, p = 1;
            while (m > (t << 1)) {
                t <<= 1;
                p <<= 1;
            }
            res += p;
            m -= t;
        }
        if ((dividend < 0) ^ (divisor < 0)) res = -res;
        return res > INT_MAX ? INT_MAX : res;
    }
};
````

