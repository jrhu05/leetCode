---
title: LeetCode刷题笔记-022GenerateParentheses
date: 2018-04-27 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

给出 n 代表生成括号的对数，请你写出一个函数，使其能够生成所有可能的并且有效的括号组合。

例如，给出 n = 3，生成结果为：

[ "((()))", "(()())", "(())()", "()(())", "()()()" ]

**分析**

一种是使用暴力法穷举所有的可能性，然后判断是否有效； 另外一种思路是使用回朔法只生成左右括号数量一致的有可能有效的组合，然后进行判断，

这会有效的减少需要判断的括号组合数量，括号有效性使用栈来解决；

**解答：**

````java
package net.jerryfu.leetCodeMedium;

import java.util.ArrayList;
import java.util.List;
import java.util.Stack;
import org.junit.Test;
public class _022GenerateParentheses {

	public List<String> generateParenthesis(int n) {
		List<String> temp = new ArrayList<String>();
		generate(temp, "", 0, 0, n);
		List<String> result = new ArrayList<String>();
		for (String str : temp) {
			if (valid(str)) {
				result.add(str);
			}
		}
		return result;
	}

	private boolean valid(String str) {
		// TODO Auto-generated method stub
		Stack<Character> operaStack = new Stack<>();
		char[] pars = str.toCharArray();
		if (str.length() <= 0) {
			return true;
		}
		operaStack.push(pars[0]);
		for (int i = 1; i < pars.length; i++) {

			if (pars[i] == '(') {
				operaStack.push(pars[i]);
			} else {
				if (!operaStack.empty()) {
					char top = operaStack.peek();
					if (top == '(' && pars[i] == ')') {
						operaStack.pop();
					} else {
						return false;
					}
				} else {
					operaStack.push(pars[i]);
				}
			}

		}
		return operaStack.empty();
	}

	private void generate(List<String> temp, String str, int lefts, int rights, int max) {
		// TODO Auto-generated method stub
		if (str.length() == 2 * max) {
			temp.add(str);
			return;
		}
		if (lefts < max) {
			generate(temp, str + "(", lefts + 1, rights, max);
		}
		if (rights < max) {
			generate(temp, str + ")", lefts, rights + 1, max);
		}
	}

	@Test
	public void test() {
		List<String> generateParenthesis = generateParenthesis(3);
		for (String string : generateParenthesis) {
			System.out.println(string);
		}
		System.out.println(generateParenthesis.size());
	}
}
````
