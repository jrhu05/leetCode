---
title: LeetCode刷题笔记-013RomanToInteger
date: 2018-02-21 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

 给定一个罗马数字，将其转换成整数。

返回的结果要求在 1 到 3999 的范围内。

**分析**

计数法
基本字符	
I	V	X	L	C	D	M
相应的阿拉伯数字表示为	
1	5	10	50	100	500	1000
相同的数字连写、所表示的数等于这些数字相加得到的数、如：Ⅲ=3；
小的数字在大的数字的右边、所表示的数等于这些数字相加得到的数、 如：Ⅷ=8、Ⅻ=12；
小的数字（限于 I、X 和 C）在大的数字的左边、所表示的数等于大数减小数得到的数、如：Ⅳ=4、Ⅸ=9；
正常使用时、连写的数字重复不得超过三次；
在一个数的上面画一条横线、表示这个数扩大 1000 倍

倒着来算有奇效^_^

**解答：**

````java
import org.junit.Test;
public class _013RomanToInteger {
	@Test
	public void test() {
		System.out.println(romanToInt("XCVIII"));
	}
	
	public int romanToInt(String s) {
		//反转
		String revStr=(new StringBuffer(s)).reverse().toString();
		char[] romanChars=revStr.toCharArray();
		int[] nums=new int[romanChars.length];
		int result=0;
		/**
		 * 计数法
			基本字符	
			I	V	X	L	C	D	M
			相应的阿拉伯数字表示为	
			1	5	10	50	100	500	1000
		 */
		for (int i = 0; i < romanChars.length; i++) {
			switch (romanChars[i]) {
			case 'I':
				nums[i]=1;
				break;
			case 'V':
				nums[i]=5;
				break;
			case 'X':
				nums[i]=10;
				break;
			case 'L':
				nums[i]=50;
				break;
			case 'C':
				nums[i]=100;
				break;
			case 'D':
				nums[i]=500;
				break;
			case 'M':
				nums[i]=1000;
				break;
			default:
				break;
			}
		}
		result=nums[0];
		for (int i = 0; i < nums.length-1; i++) {
			if (nums[i]<=nums[i+1]) {
				result+=nums[i+1];
			}else {
				result-=nums[i+1];
			}
		}
		return result;
    }
}


````









