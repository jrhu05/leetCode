---
title: LeetCode刷题笔记-017LetterCombinationsOfAPhoneNumber
date: 2018-04-21 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

给定一个仅包含数字 2-9 的字符串，返回所有它能表示的字母组合。
给出数字到字母的映射如下（与电话按键相同）。注意 1 不对应任何字母。

示例:

输入："23"
输出：["ad", "ae", "af", "bd", "be", "bf", "cd", "ce", "cf"].
说明:
尽管上面的答案是按字典序排列的，但是你可以任意选择答案输出的顺序。

**分析**

可以理解为两个层次的遍历，第一层是给定输入字符串的遍历（如“23”）；第二层是对每一个字符所对应的字母的遍历（如“2”对应的“abc”）。因此思路就是先遍历到最深层，再层层返回，遍历同层次字符

**解答：**

````java
package net.jerryfu.leetCodeMedium;

import java.util.ArrayList;
import java.util.LinkedList;
import java.util.List;

import org.junit.Test;

public class _017LetterCombinationsOfAPhoneNumber {

		String[] dict = {"","","abc","def","ghi","jkl","mno","pqrs","tuv","wxyz"};
	    public List<String> letterCombinations(String digits) {
	    	List<String> res = new ArrayList<String>();
            if(digits == null || digits.length()==0){
                return res;
            }
            backTracking(new StringBuilder(),digits,0,res);
            return res;
	    }
	    private void backTracking(StringBuilder temp,String digits,int index,List<String> res){
            if(temp.length() == digits.length()){
                res.add(temp.toString());
                return;
            }
            for(int i=0;i<dict[digits.charAt(index) - '0'].length();i++){
                temp.append(dict[digits.charAt(index)-'0'].charAt(i));
                backTracking(temp,digits,index+1,res);
                if(temp.length()>0){
                    temp.deleteCharAt(temp.length()-1);
                }
            }
        }
	

	@Test
	public void test() {
		List<String> letterCombinations = letterCombinations("234");
		for (String string : letterCombinations) {
			System.out.println(string);
		}
	}
}

````
