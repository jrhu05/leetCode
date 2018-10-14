---
title: LeetCode刷题笔记-058Length0fLastWord
date: 2018-03-13 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

给定一个字符串， 包含大小写字母、空格 ' '，请返回其最后一个单词的长度。

如果不存在最后一个单词，请返回 0 。

注意事项：一个单词的界定是，由字母组成，但不包含任何的空格。

案例:

输入: "Hello World"
输出: 5

**分析**

判断起来不难，但是要注意一些特殊的输入处理，如“”，"asd  "等

**解答：**

````java
import org.junit.Test;
public class _058Length0fLastWord {
	@Test
	public void test() {
		System.out.println(lengthOfLastWord("Hello World"));
		System.out.println(lengthOfLastWord("hello"));
		System.out.println(lengthOfLastWord("Hello World cat"));
		System.out.println(lengthOfLastWord(""));
		System.out.println(lengthOfLastWord("a"));
		System.out.println(lengthOfLastWord("asd  "));
	}
	
	public int lengthOfLastWord(String s) {
		while (s.endsWith(" ")) {
			s=s.substring(0,s.length()-1);
		}
		if (s.equals(" ")) {
			return 0;
		}
		if (!s.contains(" ")) {
			return s.length();
		}
	      int pos=s.lastIndexOf(" ");
	      return s.length()-pos-1;
	 }
}
````









