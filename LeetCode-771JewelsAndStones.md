---
title: LeetCode刷题笔记-771JewelsAndStones
date: 2018-04-01 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

给定字符串J 代表石头中宝石的类型，和字符串 S代表你拥有的石头。 S 中每个字符代表了一种你拥有的石头的类型，你想知道你拥有的石头中有多少是宝石。

J 中的字母不重复，J 和 S中的所有字符都是字母。字母区分大小写，因此"a"和"A"是不同类型的石头。

示例 1:

输入: J = "aA", S = "aAAbbbb"
输出: 3
示例 2:

输入: J = "z", S = "ZZ"
输出: 0
注意:

S 和 J 最多含有50个字母。
 J 中的字符不重复。

**分析**

easy，略

**解答：**

````java
import org.junit.Test;
public class _771JewelsAndStones {
	
	@Test
	public void test() {
		String j="z";
		String s="ZZ";
		System.out.println(numJewelsInStones(j, s));
	}
	
	 public int numJewelsInStones(String J, String S) {
		 char[] jewels=J.toCharArray();
		 char[] stones=S.toCharArray();
		 int jewelsNumber=0;
		 for (int i = 0; i < jewels.length; i++) {
			for (int k = 0; k < stones.length; k++) {
				if (jewels[i]==stones[k]) {
					jewelsNumber++;
				}
			}
		}
	     return jewelsNumber;
	 }
}

````

