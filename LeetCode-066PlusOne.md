---
title: LeetCode刷题笔记-066PlusOne
date: 2018-03-15 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

给定一个非负整数组成的非空数组，给整数加一。

可以假设整数不包含任何前导零，除了数字0本身。

最高位数字存放在列表的首位。

**分析**

除了考虑各个进位外还需要注意考虑是否有最高位的进位，如果最高位有进位，那么原各个位比为9，除此之外不需要考虑数组会增大的情况。

**解答：**

````java
import org.junit.Test;
public class _066PlusOne {
	@Test
	public void test() {
		System.out.println(Arrays.toString(plusOne(new int[]{4,9,9})));
	}
	public int[] plusOne(int[] digits) {
	       int carry = 1;

	        for (int i = digits.length - 1; i >= 0; i--) {
	            if (carry == 0) {
	                return digits;
	            }
	            int tmp = digits[i] + carry;
	            carry = tmp / 10;
	            digits[i] = tmp % 10;
	        }

	        if (carry != 0) {
	            int[] result = new int[digits.length + 1];
	            result[0] = 1;
	            return result;
	        }

	        return digits;
	    }
}

````









