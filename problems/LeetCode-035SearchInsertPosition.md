---
title: LeetCode刷题笔记-035SearchInsertPosition
date: 2018-03-07 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

给定一个排序数组和一个目标值，如果在数组中找到目标值则返回索引。如果没有，返回到它将会被按顺序插入的位置。

你可以假设在数组中无重复元素。
案例 1:
输入: [1,3,5,6], 5
输出: 2
案例 2:
输入: [1,3,5,6], 2
输出: 1
案例 3:
输入: [1,3,5,6], 7
输出: 4
案例 4:
输入: [1,3,5,6], 0
输出: 0

**分析**

easy，略

**解答：**

````java
import org.junit.Test;
public class _035SearchInsertPosition {
	@Test
	public void test() {
		System.out.println(searchInsert(new int[] {1,3,5,6}, 5));
		System.out.println(searchInsert(new int[] {1,3,5,6}, 2));
		System.out.println(searchInsert(new int[] {1,3,5,6}, 7));
		System.out.println(searchInsert(new int[] {1,3,5,6}, 0));
	}
	public int searchInsert(int[] nums, int target) {
        for (int i = 0; i < nums.length; i++) {
			if (nums[i]==target) {
				return i;
			}
		}
        if (nums[0]>=target) {
			return 0;
		}
        if (nums[nums.length-1]<target) {
			return nums.length;
		}
        for (int i = 0; i < nums.length; i++) {
			if (nums[i]>=target) {
				return i;
			}
		}
        return 0;
    }
}


````









