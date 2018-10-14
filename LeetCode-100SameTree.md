---
title: LeetCode刷题笔记-100SameTree
date: 2018-04-03 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

给定两个二叉树，编写一个函数来检验它们是否相同。

如果两个树在结构上相同，并且节点具有相同的值，则认为它们是相同的。

示例 1:

输入:       1         1
​               / \       / \
​      	     2   3     2   3

        [1,2,3],   [1,2,3]

输出: true
示例 2:

输入:      1          1
​               /           \
​             2             2

        [1,2],     [1,null,2]

输出: false
示例 3:

输入:       1         1
​               / \       / \
​             2   1     1   2

        [1,2,1],   [1,1,2]

输出: false

**分析**

主要考察二叉树的遍历

**解答：**

````java
import org.junit.Test;
public class _100SameTree {
	@Test
	public void test() {
		TreeNode t1=new TreeNode(1);
		t1.left=new TreeNode(2);
		t1.right=new TreeNode(3);
		TreeNode t2=new TreeNode(1);
		t2.left=new TreeNode(2);
		t2.right=new TreeNode(3);
		System.out.println(isSameTree(t1, t2));
		
		TreeNode t3=new TreeNode(1);
		t3.left=new TreeNode(2);
		TreeNode t4=new TreeNode(1);
		t4.right=new TreeNode(2);
		System.out.println(isSameTree(t3, t4));
		
		TreeNode t5=new TreeNode(1);
		t5.left=new TreeNode(2);
		t5.right=new TreeNode(1);
		TreeNode t6=new TreeNode(1);
		t6.left=new TreeNode(1);
		t6.right=new TreeNode(2);
		System.out.println(isSameTree(t5, t6));
	}
	/**
	 * Definition for a binary tree node.
	 * public class TreeNode {
	 *     int val;
	 *     TreeNode left;
	 *     TreeNode right;
	 *     TreeNode(int x) { val = x; }
	 * }
	 */
	public boolean isSameTree(TreeNode p, TreeNode q) {
		if (p==null&&q==null) {
			return true;
		}
		if (p==null&&q!=null) {
			return false;
		}
		if (p!=null&&q==null) {
			return false;
		}
        if (p.val!=q.val) {
			return false;
		}
	    return isSameTree(p.left, q.left)&&isSameTree(p.right, q.right);
	}
}

````

