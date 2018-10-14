---
title: LeetCode刷题笔记-018fourSum
date: 2018-04-23 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

给定一个包含 n 个整数的数组 nums 和一个目标值 target，判断 nums 中是否存在四个元素 a，b，c 和 d ，

使得 a + b + c + d 的值与 target 相等？找出所有满足条件且不重复的四元组。

注意：

答案中不可以包含重复的四元组。

示例：

给定数组 nums = [1, 0, -1, 0, -2, 2]，和 target = 0。

满足要求的四元组集合为：
[
  [-1,  0, 0, 1],
  [-2, -1, 1, 2],
  [-2,  0, 0, 2]
]

**分析**

本题可以和15题三数和问题联动，通过将四元组问题转化为三元组问题来解决，注意对重复结果的去除即可轻松解决。

**解答：**

````java
package net.jerryfu.leetCodeMedium;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.HashSet;
import java.util.LinkedList;
import java.util.List;
import org.junit.Test;

public class _018fourSum {
	
	public List<List<Integer>> threeSum(int[] nums,int target) {
		List<List<Integer>> result = new LinkedList<>();
		if (nums != null && nums.length > 2) {
			// 先对数组进行排序
			Arrays.sort(nums);
			// i表示假设取第i个数作为结果
			for (int i = 0; i < nums.length - 2;) {
				// 第二个数可能的起始位置
				int j = i + 1;
				// 第三个数可能是结束位置
				int k = nums.length - 1;

				while (j < k) {
					// 如果找到满足条件的解
					if (nums[j] + nums[k] + nums[i]==target) {
						// 将结果添加到结果含集中
						List<Integer> list = new ArrayList<>(3);
						list.add(nums[i]);
						list.add(nums[j]);
						list.add(nums[k]);
						result.add(list);

						// 移动到下一个位置，找下一组解
						k--;
						j++;

						// 从左向右找第一个与之前处理的数不同的数的下标
						while (j < k && nums[j] == nums[j - 1]) {
							j++;
						}
						// 从右向左找第一个与之前处理的数不同的数的下标
						while (j < k && nums[k] == nums[k + 1]) {
							k--;
						}
					}
					// 和大于target
					else if (nums[j] + nums[k]+ nums[i]> target) {
						k--;
						// 从右向左找第一个与之前处理的数不同的数的下标
						while (j < k && nums[k] == nums[k + 1]) {
							k--;
						}
					}
					// 和小于target
					else {
						j++;
						// 从左向右找第一个与之前处理的数不同的数的下标
						while (j < k && nums[j] == nums[j - 1]) {
							j++;
						}
					}
				}

				// 指向下一个要处理的数
				i++;
				// 从左向右找第一个与之前处理的数不同的数的下标
				while (i < nums.length - 2 && nums[i] == nums[i - 1]) {
					i++;
				}
			}
		}

		return result;
	}
	

    public List<List<Integer>> fourSum(int[] nums, int target) {
        List<List<Integer>> result=new ArrayList<List<Integer>>();
        if (nums.length<4) {
			return result;
		}
        HashSet<String> hashSet=new HashSet<>();
        Arrays.sort(nums);
        //System.out.println(Arrays.toString(nums));
        for (int i = 0; i <= nums.length-4; i++) {
			int threeSumTarget=target-nums[i];
			int[] threeScope=Arrays.copyOfRange(nums, i+1, nums.length);
			List<List<Integer>> threeSum = threeSum(threeScope, threeSumTarget);
			for (List<Integer> list : threeSum) {
				list.add(0, nums[i]);
				String fingerPrint="";
				for (Integer integer : list) {
					fingerPrint+=(integer+"");
				}
				if (!hashSet.contains(fingerPrint)) {
					hashSet.add(fingerPrint);
					result.add(list);
				}

			}
		}
        for (List<Integer> list : result) {
			System.out.println(list);
		}
    	return result;
    }
    
    

    @Test
    public void test() {
    	fourSum(new int[] {-1,-5,-5,-3,2,5,0,4,-16},-7);
    	fourSum(new int[] {0,0,0,0}, 0);
    	fourSum(new int[] {5,0,2,-5,-5,4,-5,1,-1}, -5);
    }
}
````
