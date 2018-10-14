---
title: LeetCode刷题笔记-015ThreeSum
date: 2018-04-17 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

给定一个包含 n 个整数的数组 nums，判断 nums 中是否存在三个元素 a，b，c ，使得 a + b + c = 0 ？

找出所有满足条件且不重复的三元组。

注意：答案中不可以包含重复的三元组。

例如, 给定数组 nums = [-1, 0, 1, 2, -1, -4]，

满足要求的三元组集合为： [ [-1, 0, 1], [-1, -1, 2] ]

**分析**

这题很有意思，尝试了好几次都是超时，最后参考了https://blog.csdn.net/DERRANTCM/article/details/46980229的答案。

原文给出的解法分析不是很详细，故补充如下：

首先将数组从小到大排序，从最小数开始作为三元组其中一个数，在余下的数组中找另外两个数。找另外两个数的规则是从两端向中间收缩，每次计算三数和。

如果为0那么表示找到一个满足条件的三元组，将此三元组存储到结果集中。同时，开始向内收缩，收缩的规则是最终状态为左右两端都不等于原来的数字，因为只要有一端的数字和原来数字一样，整个三元组必和找到的这个和为0的三元组完全一样（因为确定了两个数组，且和固定为0，则第三个数也确定了）。

如果大于0，则表示只有寻找一个更小的被加数才有可能使得值变为0，所以需要将最右侧的数左移，左移的规则也是找到一个和目前数字不一样的数为止。

如果小于0，则表示只有寻找一个更大的被加数才有可能使得值变为0，所以需要将最左侧数右移，右移的规则是找到一个和目前最左侧数字不一样的数字为止。

这样完成一轮第一个被加数的另外两个被加数寻找后，左移第一个被加数，直至找到和目前第一个被加数不一样的数为止，再开始新一轮的寻找。

**解答：**

````java
import java.util.ArrayList;
import java.util.Arrays;
import java.util.LinkedList;
import java.util.List;

import org.junit.Test;
public class _015ThreeSum {

	@Test
	public void test() {
		//List<List<Integer>> threeSum = threeSum(new int[] { -1, 0, 1, 2, -1, -4 });
		List<List<Integer>> threeSum = threeSum(new int[] { -2,0,1,1,2 });
		for (List<Integer> list : threeSum) {
			for (Integer integer : list) {
				System.out.print(integer + "\t");
			}
			System.out.println();
		}
	}


	public List<List<Integer>> threeSum(int[] nums) {
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
					if (nums[j] + nums[k] == -nums[i]) {
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
					// 和大于0
					else if (nums[j] + nums[k] > -nums[i]) {
						k--;
						// 从右向左找第一个与之前处理的数不同的数的下标
						while (j < k && nums[k] == nums[k + 1]) {
							k--;
						}
					}
					// 和小于0
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

}

````
