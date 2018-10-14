---
title: LeetCode刷题笔记-070ClimbingStairs
date: 2018-03-21 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

你正在爬楼梯。需要 n 步你才能到达顶部。

每次你可以爬 1 或 2 个台阶。你有多少种不同的方式可以爬到楼顶呢？

注意：给定 n 将是一个正整数。
示例 1：
输入： 2
输出： 2
说明： 有两种方法可以爬到顶端。

1.1 步 + 1 步

2.2 步

示例 2：
输入： 3
输出： 3
说明： 有三种方法可以爬到顶端。

1.1 步 + 1 步 + 1 步

2.1 步 + 2 步

3.2 步 + 1 步

**分析**

嗯，有点意思。

1个台阶是1种方法，2个台阶是2种方法，3个台阶是3种方法，4个台阶5种方法，

1,2,3,5

有点眼熟。

啊哈，斐波那契数列！

换着花样考

f(n)=f(n-1)+f(n-2)

递归法求解效率不好，太low了，直接用非递归法求解吧！

**解答：**

````java
import org.junit.Test;
public class _070ClimbingStairs {
	@Test
	public void test() {
		System.out.println(climbStairs(1));
		System.out.println(climbStairs(2));
		System.out.println(climbStairs(3));
		System.out.println(climbStairs(4));
		System.out.println(climbStairs(5));
		System.out.println(climbStairs(6));
		System.out.println(climbStairs(7));
		System.out.println(climbStairs(8));
		System.out.println(climbStairs(9));
		System.out.println(climbStairs(10));
	}
    public int climbStairs(int n) {
    	 int last=1,lastlast=1,now=0;
         if(n==0||n==1){
             return 1;
         }else{
             for(int i=2;i<=n;i++){
                 now=last+lastlast;
                 lastlast=last;
                 last=now;
             }
             return now;
         }
    }
}
````

