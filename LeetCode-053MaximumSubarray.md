---
title: LeetCode刷题笔记-053MaximumSubarray
date: 2018-03-11 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

给定一个序列（至少含有 1 个数），从该序列中寻找一个连续的子序列，使得子序列的和最大。
例如，给定序列 [-2,1,-3,4,-1,2,1,-5,4]，
连续子序列 [4,-1,2,1] 的和最大，为 6。
扩展练习:
若你已实现复杂度为 O(n) 的解法，尝试使用更为精妙的分治法求解。

**分析**

easy，略

**解答：**

````java
import org.junit.Test;
public class _053MaximumSubarray {
	@Test
	public void test() {
		System.out.println(maxSubArray(new int[] {-2,1}));
	}
	//[-2,1,-3,4,-1,2,1,-5,4]
	public int maxSubArray(int[] nums) {
		if (nums.length==1l) {
			return nums[0];
		}
	      int max=Integer.MIN_VALUE;
	      int sum=0;
	      for (int i = 0; i < nums.length; i++) {
	    	sum=nums[i];
	    	if (sum>max) {
				max=sum;
			}
			for (int j = i+1; j < nums.length; j++) {
				sum+=nums[j];
				if (sum>max) {
					max=sum;
				}
			}
		}
	      return max;
	}
}
````









