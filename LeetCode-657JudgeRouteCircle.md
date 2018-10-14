---
title: LeetCode刷题笔记-657JudgeRouteCircle
date: 2018-03-29 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

初始位置 (0, 0) 处有一个机器人。给出它的一系列动作，判断这个机器人的移动路线是否形成一个圆圈，换言之就是判断它是否会移回到原来的位置。

移动顺序由一个字符串表示。每一个动作都是由一个字符来表示的。机器人有效的动作有 R（右），L（左），U（上）和 D（下）。输出应为 true 或 false，表示机器人移动路线是否成圈。

示例 1:

输入: "UD"
输出: true

示例 2:

输入: "LL"
输出: false

**分析**

如果能成圈的话，那么UD、LR必须是成对出现的，一种解决思路是统计U、D、L、R出现的次数，如果U、D的次数一样且L、R的次数一样，那么可以成圈

鸡贼的做法是，赋予U/D、L/R正负对应的值，拉开两组值的绝对值差，然后加加减减，最后为0即可，嘻嘻

**解答：**

````java
import org.junit.Test;
public class _657JudgeRouteCircle {
	
	@Test
	public void test() {
		String route="RDRUULLD";
		System.out.println(judgeCircle(route));
	}
	
	 public boolean judgeCircle(String moves) {
	        char[] steps=moves.toCharArray();
	        int total=0;
	        for (int i = 0; i < steps.length; i++) {
				switch (steps[i]) {
				case 'U':
					total+=1;
					break;
				case 'D':
					total-=1;
					break;
				case 'R':
					total+=100;
					break;
				case 'L':
					total-=100;
					break;
				default:
					break;
				}
			}
	        if (total==0) {
				return true;
			}
	        return false;
	  }
}
````

