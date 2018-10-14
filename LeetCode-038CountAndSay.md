---
title: LeetCode刷题笔记-LeetCode刷题笔记-038CountAndSay
date: 2018-03-09 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

数数并说序列是一个整数序列，第二项起每一项的值为对前一项的计数，其前五项如下：

1.1

2.11

3.21

4.1211

5.111221
1 被读作 "一个一" 即 11。
11 被读作  "两个一" 即 21。
21 被读作  "一个二 和 一个一" 即 1211。
给一个正整数 n ，输出数数并说序列的第 n 项。
注意：该整数序列的每项都输出为字符串。
例 1:
输入: 1
输出: "1"
例 2:
输入: 4
输出: "1211"
The following are the terms from n=1 to n=10 of the count-and-say sequence:

1.1

2.11

3.21

4.1211

5.111221 

6.312211

7.13112221

8.1113213211

9.31131211131221

10.13211311123113112211

**分析**

递归求解

**解答：**

````java
import org.junit.Test;
public class _038CountAndSay {
	@Test
	public void test() {
		//read("1211");
		System.out.println(countAndSay(9));
		//countAndSay(3);
	}
	 public String countAndSay(int n) {
	    if (n==1) {
			return "1";
		}
	    return read(countAndSay(n-1));
	 }
	 
	 
	 public String read(String needToReadStr) {
		 //11
		 int[] need2Read=new int[needToReadStr.length()];
		 for (int i = 0; i < needToReadStr.length(); i++) {
			need2Read[i]=Integer.valueOf(needToReadStr.charAt(i)+"");
		}
		 int index=0;
		 StringBuffer sb=new StringBuffer();
		 while (index<need2Read.length) {
			int count=0;
			//11
			for (int i = index; i < need2Read.length; i++) {
				if (need2Read[index]==need2Read[i]) {
//					System.out.println("index-->"+index+"-->"+need2Read[index]);
//					System.out.println("i-->"+i+"-->"+need2Read[i]);
					count++;
				}else {
					index=i;
					break;
				}
				if (index==need2Read.length-1) {
					index=need2Read.length;
				}
				if (i==need2Read.length-1) {
					index=need2Read.length;
				}
			}
			if (index==0) {
				sb.append(count).append(need2Read[index]);
			}else {
				sb.append(count).append(need2Read[index-1]);
			}
			
		}
		 return sb.toString();
	 }
	 
}
````









