---
title: LeetCode刷题笔记-088MergeSortedArray
date: 2018-03-25 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

给定两个有序整数数组 nums1 和 nums2，将 nums2 合并到 nums1中，使得 num1 成为一个有序数组。

注意:

你可以假设 nums1有足够的空间（空间大小大于或等于m + n）来保存 nums2 中的元素。在 nums1 和 nums2 中初始化的元素的数量分别是 m 和 n。

**分析**

注意考虑如何向num1数组适当位置插入两个数组的数，可以从后向前考虑，优先放置num1数组中的数，这就无需移位处理。此外因为数组本身有序，所以最后只需要考虑num2长度比num1长度大的情况，即代码中的

````java
while ( j >= 0){
	            nums1[k--] = nums2[j--];
	        }
````

**解答：**

````java
import org.junit.Test;
public class _088MergeSortedArray {
	@Test
	public void test() {
//		int[] num1=new int[10];
//		num1[0]=1;
//		num1[1]=1;
//		num1[2]=2;
//		num1[3]=3;
//		num1[4]=5;
//		int[] num2=new int[] {1,2,4,5,10};
//		merge(num1, 10, num2, 5);
		
		int[] num1=new int[9];
		num1[0]=-1;
		num1[1]=0;
		num1[2]=0;
		num1[3]=3;
		num1[4]=3;
		num1[5]=3;
		int[] num2=new int[] {1,2,2};
		merge(num1, 6, num2, 3);
	}
	public void merge(int[] nums1, int m, int[] nums2, int n) {
		 int i = m -1;
	        int j = n -1;
	        int k = m + n -1;
	        while ( i >= 0 && j >= 0){
	            if (nums1[i] > nums2[j]){
	                nums1[k--] = nums1[i--];
	            }else{
	                nums1[k--] = nums2[j--];
	            }
	        }

	        while ( j >= 0){
	            nums1[k--] = nums2[j--];
	        }
	    }
	}
````

