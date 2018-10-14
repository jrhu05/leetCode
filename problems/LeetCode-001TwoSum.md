---
title: LeetCode刷题笔记-001TwoSum
date: 2018-02-13 09:00:37
categories: 算法寻径
tags: [LeetCode]
---

**题目：**

给定一个整数数列，找出其中和为特定值的那两个数。

你可以假设每个输入都只会有一种答案，同样的元素不能被重用。

示例:

给定 nums = [2, 7, 11, 15], target = 9

因为 nums[0] + nums[1] = 2 + 7 = 9
所以返回 [0, 1]

**分析**

本题很简单，分析略

**解答：**

````java
import org.junit.Test;
public class _001TwoSum {
	
	@Test
	public void test() {
		int[] nums= {3,2,4};
		System.out.println(Arrays.toString(twoSum(nums, 6)));
	}
	
	
    public int[] twoSum(int[] nums, int target) {
       for (int i = 0; i < nums.length; i++) {
		int temp=target-nums[i];
		for (int j = i+1; j < nums.length; j++) {
			if (temp==nums[j]) {
				 int[] result={i,j};
				return result;
			}
		}
	}
       return new int[] {0,0};
    }
}
````









