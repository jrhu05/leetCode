---
title: LeetCode刷题笔记-031NextPermutation
date: 2018-05-05 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

实现获取下一个排列的函数，算法需要将给定数字序列重新排列成字典序中下一个更大的排列。

如果不存在下一个更大的排列，则将数字重新排列成最小的排列（即升序排列）。

必须原地修改，只允许使用额外常数空间。

以下是一些例子，输入位于左侧列，其相应输出位于右侧列。
1,2,3 → 1,3,2
3,2,1 → 1,2,3
1,1,5 → 1,5,1

**分析**

https://leetcode-cn.com/problems/next-permutation/solution/

**解答：**

````java
package net.jerryfu.leetCodeMedium;

import java.util.Arrays;
import org.junit.Test;
public class _031NextPermutation {

	public void nextPermutation(int[] nums) {
		int i=nums.length-2;
		while (i>=0&&nums[i+1]<=nums[i]) {
			i--;
		}
		if (i>=0) {
			int j=nums.length-1;
			while(j>=0&&nums[j]<=nums[i]) {
				j--;
			}
			swap(nums,i,j);
		}
		reverse(nums,i+1);
	}

	private void reverse(int[] nums, int start) {
		// TODO Auto-generated method stub
		int i=start,j=nums.length-1;
		while (i<j) {
			swap(nums, i, j);
			i++;
			j--;
		}
	}

	private void swap(int[] nums, int i,int j) {
		// TODO Auto-generated method stub
		int temp=nums[i];
		nums[i]=nums[j];
		nums[j]=temp;
	}
	
	@Test
	public void test() {
		int[] nums=new int[]{1,2,3};
		nextPermutation(nums);
		System.out.println(Arrays.toString(nums));
	}
	
}

````

