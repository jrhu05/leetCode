---
title: LeetCode刷题笔记-028ImplementStrstr
date: 2018-03-05 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

实现 strStr()。

返回蕴含在 haystack 中的 needle 的第一个字符的索引，如果 needle 不是 haystack 的一部分则返回 -1 。

例 1:

输入: haystack = "hello", needle = "ll"
输出: 2


例 2:

输入: haystack = "aaaaa", needle = "bba"
输出: -1

**分析**

easy，略

**解答：**

````java
import org.junit.Test;
public class _028ImplementStrstr {
	@Test
	public void test() {
		/**\
		 * "mississippi"
			"issip"
		 */
//		System.out.println(strStr("hello", "ll"));
//		System.out.println(strStr("aaaaa","bba"));
		System.out.println(strStr("", ""));
		System.out.println(strStr("", "a"));
		System.out.println(strStr("aaa", "aaaa"));
		System.out.println(strStr("mississippi", "issip"));
	}
	 public int strStr(String haystack, String needle) {
		 if (needle.equals("")) {
			return 0;
		}
		 if (!haystack.contains(needle)) {
			return -1;
		}
	        return haystack.indexOf(needle);
	 }
}


````









