---
title: LeetCode刷题笔记-033SearchInRotatedSortedArray
date: 2018-05-07 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

假设按照升序排序的数组在预先未知的某个点上进行了旋转。

( 例如，数组 [0,1,2,4,5,6,7] 可能变为 [4,5,6,7,0,1,2] )。

搜索一个给定的目标值，如果数组中存在这个目标值，则返回它的索引，否则返回 -1 。

你可以假设数组中不存在重复的元素。

你的算法时间复杂度必须是 O(log n) 级别。

示例 1:

输入: nums = [4,5,6,7,0,1,2], target = 0
输出: 4
示例 2:

输入: nums = [4,5,6,7,0,1,2], target = 3
输出: -1

**分析**

题目乍看很复杂，不过弄明白后很简单。最开始的思路是把序列还原成正确的升序序列再二分查找，结果发现还原的消耗很高，无法达到题目的要求。

那么能否直接对原序列进行二分查找呢？整个序列我们可以看成两个升序序列，从二分法入手，那么中间的mid对应的数可能有两种情况。

一种情况是比第一个数大：这种情况表明start到mid点中间是一段有效的递增序列，此时如果目标值（target）满足不小于start点值同时比mid点值小，则说明该目标值在mid左侧的区间里，则更新end为mid左侧的第一个点，缩小查找范围。如果目标值不满足上述条件则并不能说明该数查找不到，因为即使target点值比start点值小，mid右侧的序列中也可能有该值，所以需要右移start到mid的右侧第一个点，在右侧的区间继续进行查找；

另外一种情况比第一个数小：这种情况表明mid到end点中间是一段有效的递增序列，此时如果目标值满足比mid点值大同时不大于end点值，则说明目标值一定在mid右侧的区间里，则右移start到mid的右侧第一个点，缩小查找范围。如果目标值不满足上述条件同样也并不能说明该数查找不到，因为即使target点值比end点值大，mid左侧的序列中也可能有改值，所以需要左移end到mid左侧第一个点，在左侧的区间继续进行查找。

参考：https://blog.csdn.net/whdAlive/article/details/80432797

**解答：**

````java
package net.jerryfu.leetCodeMedium;

import org.junit.Test;

public class _033SearchInRotatedSortedArray {

	 public int search(int[] nums, int target) {
		 if (nums.length==0) {
			return -1;
		}
		 int start=0,end=nums.length-1;
		 while (start<=end) {
			int mid=start+(end-start)/2;
			if (nums[mid]==target) {
				return mid;
			}
			if (nums[mid]>=nums[start]) {
				if (nums[start]<=target&&target<nums[mid]) {
					end=mid-1;
				}else {
					start=mid+1;
				}
			}else {
				if (nums[mid]<target&&target<=nums[end]) {
					start=mid+1;
				}else {
					end=mid-1;
				}
			}
		}
	      return -1;  
	 }

	 @Test
	 public void test() {
		 int[] nums=new int[]{4,5,6,7,0,1,2};
		 System.out.println(search(nums, 0));
		 System.out.println(search(nums, 3));
		 System.out.println(search(nums, 4));
	 }
}


````

