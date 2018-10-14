---
title: LeetCode刷题笔记-069Sqrtx
date: 2018-03-19 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

实现 int sqrt(int x) 函数。

计算并返回 x 的平方根。

x 保证是一个非负整数。

案例 1:
输入: 4
输出: 2
案例 2:
输入: 8
输出: 2
说明: 8 的平方根是 2.82842..., 由于我们想返回一个整数，小数部分将被舍去

**分析**

题目要求的是整数，所以就没必要用二分逼近法或牛顿迭代法，怎么简单怎么来__(:з」∠)_

**解答：**

````java
import org.junit.Test;
public class _069Sqrtx {
	@Test
	public void test() {
		System.out.println(mySqrt(1));
		System.out.println(mySqrt(2));
		System.out.println(mySqrt(3));
		System.out.println(mySqrt(4));
		System.out.println(mySqrt(5));
		System.out.println(mySqrt(6));
		System.out.println(mySqrt(7));
		System.out.println(mySqrt(8));
		System.out.println(mySqrt(9));
		System.out.println(mySqrt(1024));
		System.out.println(mySqrt(2147483647));
		System.out.println(46340*46340);
	}
	public int mySqrt(int x) {
		long xlong=x;
		if (x==1) {
			return 1;
		}
	    for(long i=0;i<=x/2+1;i++) {
	    	if (i*i==x) {
				return (int) i;
			}
	    	if (i*i>x) {
				return (int) (i-1);
			}
	    	//System.out.println("i*i="+i*i);
	    } 
	    return -1;
	}
}


````









