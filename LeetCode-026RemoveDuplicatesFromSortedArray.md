---
title: LeetCode刷题笔记-026RemoveDuplicatesFromSortedArray
date: 2018-03-01 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

 给定一个有序数组，你需要原地删除其中的重复内容，使每个元素只出现一次,并返回新的长度。

不要另外定义一个数组，您必须通过用 O(1) 额外内存原地修改输入的数组来做到这一点。

示例：

给定数组: nums = [1,1,2],

你的函数应该返回新长度 2, 并且原数组nums的前两个元素必须是1和2
不需要理会新的数组长度后面的元素

**分析**

鸡贼的做法：归零重排序（因为测试用例里也出现了0所以用Integer.MAX_VALUE来替代作为标记）

**解答：**

````java
import org.junit.Test;
public class _026RemoveDuplicatesFromSortedArray {
	@Test
	public void test() {
			System.out.println(removeDuplicates(new int[] {1,1,2,2,3,4,5,6,7,7,8,9}));
	}
	public int removeDuplicates(int[] nums) {
		int count=0;
	     for (int i = 0; i < nums.length; i++) {
			for (int j = i+1; j < nums.length; j++) {
				if (nums[j]!=Integer.MAX_VALUE&&nums[j]==nums[i]) {
					nums[j]=Integer.MAX_VALUE;
					count++;
				}
			}
		}  
	     count=nums.length-count;
	     for (int i = 0; i < nums.length; i++) {
			if (nums[i]==Integer.MAX_VALUE) {
				for (int j = i; j < nums.length; j++) {
					if (nums[j]!=Integer.MAX_VALUE) {
						nums[i]=nums[j];
						nums[j]=Integer.MAX_VALUE;
						break;
					}
				}
			}
		}
	    System.out.println(Arrays.toString(nums));
	    return count;
	}
}

````









