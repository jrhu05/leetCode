---
title: LeetCode刷题笔记-014LongestCommonPrefix
date: 2018-02-23 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

 编写一个函数来查找字符串数组中最长的公共前缀字符串。

**分析**

easy，略

**解答：**

````java
import org.junit.Test;
public class _014LongestCommonPrefix {
	@Test
	public void test() {
		String[] strs= {"aba","aa"};
		System.out.println(longestCommonPrefix(strs));
		
		
	}
	
	public String longestCommonPrefix(String[] strs) {
		//找到最长串
		String maxLenStr="";
		for (int i = 0; i < strs.length; i++) {
			if (strs[i].length()>maxLenStr.length()) {
				maxLenStr=strs[i];
			}
		}
		//开始比对
		if (maxLenStr.equals("")) {
			return "";
		}
		String resultStr="";//从第一个字符开始
		if (maxLenStr.length()==1) {
			//特殊情况
			for (int i = 0; i < strs.length; i++) {
				if (!maxLenStr.equals(strs[i])) {
					return "";
				}
			}
			return maxLenStr;
		}
		for (int i = 0; i <= maxLenStr.length(); i++) {
			resultStr=maxLenStr.substring(0, i);
			for (int j = 0; j < strs.length; j++) {
				if (!strs[j].startsWith(resultStr)) {
					return resultStr.substring(0,resultStr.length()-1);
				}
			}
		}
	     return resultStr;   
	}
}

````









