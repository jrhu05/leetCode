---
title: LeetCode刷题笔记-461HammingDistance
date: 2018-03-27 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

两个整数之间的汉明距离指的是这两个数字对应二进制位不同的位置的数目。

给出两个整数 x 和 y，计算它们之间的汉明距离。

注意：
0 ≤ x, y < 231.

示例:

输入: x = 1, y = 4

输出: 2

解释:
1   (0 0 0 1)
4   (0 1 0 0)
​      	 ↑     ↑

上面的箭头指出了对应二进制位不同的位置

**分析**

easy，略

**解答：**

````java
import org.junit.Test;
public class _461HammingDistance {
	
	@Test
	public void test() {
		System.out.println(hammingDistance(1, 4));
	}
	
	 public int hammingDistance(int x, int y) {
	    String binX=new StringBuffer(Integer.toBinaryString(x)).reverse().toString();
	    String binY=new StringBuffer(Integer.toBinaryString(y)).reverse().toString();
	    //System.out.println(binX);
	    //System.out.println(binY);
	    int minLength=binX.length()>=binY.length()?binY.length():binX.length();
	    int total=0;
	    for (int i = 0; i < minLength; i++) {
			if (binX.charAt(i)!=binY.charAt(i)) {
				total++;
			}
		}
	    //System.out.println("total->"+total);
	    int sub=0;
	    String maxStr=(binX.length()>=binY.length())?binX:binY;
	    //System.out.println(minLength+"-->"+maxStr.length());
	    for (int i = minLength; i < maxStr.length(); i++) {
			if (maxStr.charAt(i)!='0') {
				sub++;
			}
		}
	   // System.out.println("sub->"+sub);
	    return total+sub;
	 }
}

````

