---
title: LeetCode刷题笔记-034FindFirstAndLastPositionOfElementInSortedArray
date: 2018-05-09 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

给定一个按照升序排列的整数数组 nums，和一个目标值 target。找出给定目标值在数组中的开始位置和结束位置。

你的算法时间复杂度必须是 O(log n) 级别。

如果数组中不存在目标值，返回 [-1, -1]。

示例 1:

输入: nums = [5,7,7,8,8,10], target = 8
输出: [3,4]
示例 2:

输入: nums = [5,7,7,8,8,10], target = 6
输出: [-1,-1]

**分析：**

二分法查找到目标值，然后左右扩展找到边界即可。

**解答：**

````java
package net.jerryfu.leetCodeMedium;

import java.util.Arrays;

import org.junit.Test;

public class _034FindFirstAndLastPositionOfElementInSortedArray {

	public int[] searchRange(int[] nums, int target) {
	    int position=binarySearch(nums, target);
	    if (position==-1) {
			return new int[] {position,position};
		}
	    int left=position;
	    int right=position;
	    while (left>0) {
			if (nums[left-1]==nums[position]) {
				left--;
			}else {
				break;
			}
		}
	    while (right<nums.length-1) {
			if (nums[right+1]==nums[position]) {
				right++;
			}else {
				break;
			}
		}
		return new int[] {left,right};
	}
	
	public int binarySearch(int[] nums,int target) {
		int start=0;
		int end=nums.length-1;
		while (start<=end) {
			int mid=start+(end-start)/2;
			if (nums[mid]==target) {
				return mid;
			}
			if (nums[mid]<target) {
				start=mid+1;
			}else {
				end=mid-1;
			}
		}
		return -1;
	}

	@Test
	public void test() {
		int[] nums=new int[] {5,7,7,8,8,10};
		System.out.println(binarySearch(nums, 10));
		System.out.println(Arrays.toString(searchRange(nums, 10)));
		System.out.println(Arrays.toString(searchRange(nums, 5)));
	}
}

````

