---
title: LeetCode刷题笔记-004LongestPalindromicSubstring
date: 2018-04-07 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

给定一个字符串 s，找到 s 中最长的回文子串。你可以假设 s 的最大长度为1000。

示例 1：

输入: "babad"
输出: "bab"
注意: "aba"也是一个有效答案。
示例 2：

输入: "cbbd"
输出: "bb"

**分析**

思路1：最简单的，遍历字符串的**“所有子串”**，并判断每个子串是否为对称回文。可以优化点：从最长的子串开始遍历，一旦找到一个回文，就终止迭代；判断回文采用收缩法。从最外一对字符往中心推进。

思路2：从字符的中心开始，向两边扩散检查回文。这需要维护一个指针，从头开始，以每一个位置为中心遍历一遍。这比暴力遍历所有子串省了很多重复判断。以某个字符为核心一旦探测到边界，更长的的串就都不再考虑。

思路3：Manacher算法

**解答：**

````java
import org.junit.Test;
public class _004LongestPalindromicSubstring {
	@Test
	public void test() {
		//longestPalindrome("cbbd");
//		System.out.println(isPalindrome("aba"));
//		System.out.println(isPalindrome("abba"));
//		System.out.println(isPalindrome("asdasdqeqw"));
//		System.out.println(isPalindrome("a"));
//		System.out.println(isPalindrome("aa"));
		
		System.out.println(longestPalindrome("babad"));
		System.out.println(longestPalindrome("cbbd"));
	}
    public String longestPalindrome(String s) {
        if (s==null||s.length()<=1) {
			return s;
		}
        //取子串
        String longestStr="";
        //int maxLong=longestStr.length();
        for (int i = 0; i < s.length(); i++) {
			for (int j = s.length(); j >i; j--) {
				if (j-i>longestStr.length()) {
					String subStr=s.substring(i, j);
					//System.out.println(subStr);
					if (isPalindrome(subStr)) {
						if (subStr.length()>longestStr.length()) {
							longestStr=subStr;
						}
					}
				}
			}
		}
        return longestStr;
    }
	private boolean isPalindrome(String subStr) {
		// TODO Auto-generated method stub
		//aba
		//abba
		int times=(int) Math.ceil(subStr.length()/2.0);
		//System.out.println(times);
		for (int i = 0; i < subStr.length()/2; i++) {
			if (subStr.charAt(i)!=subStr.charAt(subStr.length()-i-1)) {
				return false;
			}
		}
		return true;
	}
}

````









