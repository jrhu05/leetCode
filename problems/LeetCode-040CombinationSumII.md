---
title: LeetCode刷题笔记-040CombinationSumII
date: 2018-07-17 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

给定一个数组 candidates 和一个目标数 target ，找出 candidates 中所有可以使数字和为 target 的组合。

candidates 中的每个数字在每个组合中只能使用一次。

说明：

所有数字（包括目标数）都是正整数。
解集不能包含重复的组合。 
示例 1:

输入: candidates = [10,1,2,7,6,1,5], target = 8,
所求解集为:
[
  [1, 7],
  [1, 2, 5],
  [2, 6],
  [1, 1, 6]
]
示例 2:

输入: candidates = [2,5,2,1,2], target = 5,
所求解集为:
[
  [1,2,2],
  [5]
]

**分析：**

使用回溯法求解
详细可参考https://blog.csdn.net/xuyueqing1225/article/details/70574834

**解答：**

````java
package net.jerryfu.leetCodeMedium;

import java.util.ArrayList;
import java.util.List;
import org.junit.Test;

public class _040CombinationSumII {

	private List<List<Integer>> result = new ArrayList<List<Integer>>();

	public List<List<Integer>> combinationSum2(int[] candidates, int target) {
		Arrays.sort(candidates);
		System.out.println(Arrays.toString(candidates));
		findanswer(0, new ArrayList<Integer>(), candidates, target);
		return result;
	}

	public void findanswer(int index, List<Integer> ans, int[] candidates, int target) {
		while (index < candidates.length && candidates[index] <= target) {
			if (candidates[index] <= target / 2) {
				List<Integer> l1 = new ArrayList<Integer>(ans);
				l1.add(candidates[index]);
				// index从变为index+1
				findanswer(index + 1, l1, candidates, target - candidates[index]);
			}
			if (candidates[index] == target) {
				List<Integer> l1 = new ArrayList<Integer>(ans);
				l1.add(candidates[index]);
				result.add(l1);
			}
			// 当下一个数与当前数相同时，跳过
			while (++index < candidates.length && candidates[index] == candidates[index - 1])
				;
		}
	}


	@Test
	public void test() {
		int[] candidates=new int[] {10,1,2,7,6,1,5};
		int target=8;
		List<List<Integer>> result = combinationSum2(candidates, target);
		for (List<Integer> list : result) {
			System.out.println(list);
		}
	}
}
````

