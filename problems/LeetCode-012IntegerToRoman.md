---
title: LeetCode刷题笔记-012IntegerToRoman
date: 2018-04-15 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

罗马数字包含以下七种字符： I， V， X， L，C，D 和 M。

字符         数值
I            	1
V            	5
X            	10
L             	50
C             100
D             500
M            1000
例如， 罗马数字 2 写做 II ，即为两个并列的 1。12 写做 XII ，即为 X + II 。 27 写做  XXVII, 即为 XX + V + II 。

通常情况下，罗马数字中小的数字在大的数字的右边。但也存在特例，例如 4 不写做 IIII，而是 IV。数字 1 在数字 5 的左边，所表示的数等于大数 5 减小数 1 得到的数值 4 。同样地，数字 9 表示为 IX。这个特殊的规则只适用于以下六种情况：

I 可以放在 V (5) 和 X (10) 的左边，来表示 4 和 9。
X 可以放在 L (50) 和 C (100) 的左边，来表示 40 和 90。 
C 可以放在 D (500) 和 M (1000) 的左边，来表示 400 和 900。
给定一个整数，将其转为罗马数字。输入确保在 1 到 3999 的范围内。

示例 1:

输入: 3
输出: "III"

示例 2:

输入: 4
输出: "IV"

示例 3:

输入: 9
输出: "IX"

示例 4:

输入: 58
输出: "LVIII"
解释: C = 100, L = 50, XXX = 30, III = 3.

示例 5:

输入: 1994
输出: "MCMXCIV"
解释: M = 1000, CM = 900, XC = 90, IV = 4.

**分析**

从千分为开始，一步步拼接，注意4、9、40、90、400、900需要进行特殊处理。

**解答：**

````java
import org.junit.Test;

public class _012IntegerToRoman {
	
	@Test
	public void test() {
		System.out.println(intToRoman(3));
		System.out.println(intToRoman(4));
		System.out.println(intToRoman(9));
		System.out.println(intToRoman(58));
		System.out.println(intToRoman(1994));
		System.out.println(intToRoman(3999));
	}
	 public String intToRoman(int num) {
	        /**
	         * 	I             1
				V             5
				X             10
				L             50
				C             100
				D             500
				M             1000
	         */
		 StringBuffer sb=new StringBuffer();
		 int thousands=num/1000;
		 int thousandsTemp=thousands;
		 for (int i = 0; i < thousands; i++) {
			sb.append("M");
		}
		 num=num-1000*thousandsTemp;
		 /**
		  * I 可以放在 V (5) 和 X (10) 的左边，来表示 4 和 9。
			X 可以放在 L (50) 和 C (100) 的左边，来表示 40 和 90。 
			C 可以放在 D (500) 和 M (1000) 的左边，来表示 400 和 900。
		  */
		 int hundreds=num/100;
		 int hundredstemp=hundreds;
		 if (hundreds==9) {
			sb.append("CM");
		}else if (hundreds==4) {
			sb.append("CD");
		}else {
			if (hundreds>=5) {
				sb.append("D");
				hundreds=hundreds-5;
			}
			for (int i = 0; i < hundreds; i++) {
				sb.append("C");
			}
		}
		 num=num-100*hundredstemp;
		 int tens=num/10;
		 int tensTemp=tens;
		 if (tens==9) {
			sb.append("XC");
		}else if (tens==4) {
			sb.append("XL");
		}else {
			if (tens>=5) {
				sb.append("L");
				tens=tens-5;
			}
			for (int i = 0; i < tens; i++) {
				sb.append("X");
			}
		}
		 int units=num-10*tensTemp;
		 if (units==9) {
			sb.append("IX");
		}else if (units==4) {
			sb.append("IV");
		}else {
			if (units>=5) {
				sb.append("V");
				units=units-5;
			}
			for (int i = 0; i < units; i++) {
				sb.append("I");
			}
		}
		 return sb.toString();
	 }

}


````









