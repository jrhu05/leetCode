---
title: LeetCode刷题笔记-020ValidParentheses
date: 2018-02-25 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

给定一个只包括 '('，')'，'{'，'}'，'['，']' 的字符串，判断字符串是否有效。

括号必须以正确的顺序关闭，"()" 和 "()[]{}" 是有效的但是 "(]" 和 "([)]" 不是。

**分析**

经典的栈的应用，依次入栈，如果栈顶元素和需要入栈的元素能配对则pop出栈栈顶元素，最后判断栈是否为空，为空则说明配对成功，字符串有效。

**解答：**

````java
import org.junit.Test;
public class _020ValidParentheses {
	@Test
	public void test() {
		System.out.println(isValid("()[]{}"));
		System.out.println(isValid("([)]"));
		System.out.println(isValid(""));
		System.out.println("");
		System.out.println(isValid("{"));
		System.out.println(isValid(")"));
		System.out.println(isValid("[])"));
	}
	
	public boolean isValid(String s) {
	   Stack<Character> operaStack=new Stack<>();
	   char[] pars=s.toCharArray();
	   if (s.length()<=0) {
		return true;
	   }
	   operaStack.push(pars[0]);
	   for (int i = 1; i < pars.length; i++) {
		   if (pars[i]=='('||pars[i]=='{'||pars[i]=='[') {
			   operaStack.push(pars[i]);
		   }else {
			   if (!operaStack.empty()) {
				   char top=operaStack.peek();
				   if ((top=='('&&pars[i]==')')||
						(top=='{'&&pars[i]=='}') ||
						top=='['&&pars[i]==']') {
					   operaStack.pop();
				   }else {
					   return false;
				   }
			   }else {
				   operaStack.push(pars[i]);
			}
		   }
	   }
	   return operaStack.empty();
	}
}

````









