---
title: LeetCode刷题笔记-007ReverseInteger
date: 2018-02-17 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

给定一个范围为 32 位 int 的整数，将其颠倒。

例 1:
输入: 123
输出:  321
例 2:
输入: -123
输出: -321
例 3:
输入: 120
输出: 21

**分析**

本题较为简单，故略。

**解答：**

````java
import org.junit.Test;
public class _007ReverseInteger {
	@Test
	public void test() {
		System.out.println(reverse(120));
	}
	public int reverse(int x) {
		try {
			String reverseStr =  new StringBuffer(Integer.toString(x)).reverse().toString();
		     //System.out.println(reverseStr);
		     if (x<0) {
				reverseStr=reverseStr.substring(0,reverseStr.length()-1);
			}
		     //System.out.println(reverseStr);
		     int result=Integer.parseInt(reverseStr);
		     if (x<0) {
		    	 return -result;
			}
		     return result;
		}catch (Exception e) {
			// TODO: handle exception
			return 0;
		}
	     
	}
}

````









