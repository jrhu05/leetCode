---
title: LeetCode刷题笔记-027RemoveElement
date: 2018-03-03 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

给定一个数组和一个值，在这个数组中原地移除指定值和返回移除后新的数组长度。

不要为其他数组分配额外空间，你必须使用 O(1) 的额外内存原地修改这个输入数组。

元素的顺序可以改变。超过返回的新的数组长度以外的数据无论是什么都没关系。

示例:

给定 nums = [3,2,2,3]，val = 3，

你的函数应该返回 长度 = 2，数组的前两个元素是 2。

**分析**

easy，还是使用Integer.MAX_VALUE来替代作为标记

**解答：**

````java
import org.junit.Test;
public class _027RemoveElement {
	@Test
	public void test() {
		System.out.println(removeElement(new int[]{3,2,7,3,5,2,3},3));
	}
	
	public int removeElement(int[] nums, int val) {
		int count=0;
	     for (int i = 0; i < nums.length; i++) {
				if (nums[i]!=Integer.MAX_VALUE&&nums[i]==val) {
					nums[i]=Integer.MAX_VALUE;
					count++;
			}
		}  
	     //System.out.println(count);
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
		//System.out.println(Arrays.toString(nums));
	   return count;
	}
}

````









