---
title: LeetCode刷题笔记-003LongestSubstringWithoutRepeatingCharacters
date: 2018-04-05 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

给定一个字符串，找出不含有重复字符的最长子串的长度。

示例：

给定 "abcabcbb" ，没有重复字符的最长子串是 "abc" ，那么长度就是3。

给定 "bbbbb" ，最长的子串就是 "b" ，长度是1。

给定 "pwwkew" ，最长子串是 "wke" ，长度是3。请注意答案必须是一个子串，"pwke" 是 子序列  而不是子串。

**分析**

注意子串的获取

**解答：**

````java
import org.junit.Test;
public class _003LongestSubstringWithoutRepeatingCharacters {
	@Test
	public void test() {
		 System.out.println(lengthOfLongestSubstring("abcabcbb"));//3
		 System.out.println(lengthOfLongestSubstring("bbbbb"));//1
		 System.out.println(lengthOfLongestSubstring("pwwkew"));//3
		 System.out.println(lengthOfLongestSubstring("dvdf"));//3
	}
	public int lengthOfLongestSubstring(String s) {
	        if (s==null||s.equals("")) {
				return 0;
			}
	        if (s.length()==1) {
				return 1;
			}
	        int i=0,j=1;
	        int max=1;
	        ArrayList<Character> characters=new ArrayList<>();
	        characters.add(s.charAt(i));
	        int tempMax=1;
	        while (j<s.length()) {
	        	//dvdf
				if (!characters.contains(s.charAt(j))) {
					characters.add(s.charAt(j));
					//System.out.println(s.charAt(j));
					tempMax++;
					//System.out.println("tempMax->"+tempMax);
				}else {
					//pwwkew
					i++;
					j=i;
					characters=new ArrayList<>();
					characters.add(s.charAt(j));
					tempMax=1;
				}
				if (tempMax>max) {
					max=tempMax;
				}
				j++;
			}
	        return max;
	}
}

````









