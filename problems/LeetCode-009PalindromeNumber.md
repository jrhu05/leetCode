---
title: LeetCode刷题笔记-009PalindromeNumber
date: 2018-02-19 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

 判断一个整数是否是回文数。不能使用辅助空间。

点击查看提示

一些提示:

负整数可以是回文数吗？（例如 -1）

如果你打算把整数转为字符串，请注意不允许使用辅助空间的限制。

你也可以考虑将数字颠倒。但是如果你已经解决了 “颠倒整数” 问题的话，就会注意到颠倒整数时可能会发生溢出。你怎么来解决这个问题呢？

本题有一种比较通用的解决方式。

**分析**

负整数不能是回文数，从两端开始比较最高位和最低位的数字是否一致，直至结束，如全部一致那么就是回文数，否则不是。

**解答：**

````java
import org.junit.Test;
public class _009PalindromeNumber {
	@Test
	public void test() {
		System.out.println(isPalindrome(1212));
	}
	 public boolean isPalindrome(int x) {
		 if (x < 0)
	    return false;
	    int div = 1;
	    while (x / div >= 10)
	    {
	        div *= 10;
	    }
	 
	    while (x != 0)
	    {
	        int l = x / div;
	        int r = x % 10;
	        if (l != r)
	            return false;
	        x = (x % div) / 10;
	        div /= 100;
	    }
	    return true;
	 }
}


````









