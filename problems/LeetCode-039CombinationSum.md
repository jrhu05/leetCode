---
title: LeetCode刷题笔记-039CombinationSum
date: 2018-06-12 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

给定一个无重复元素的数组 candidates 和一个目标数 target ，找出 candidates 中所有可以使数字和为 target 的组合。

candidates 中的数字可以无限制重复被选取。

说明：

所有数字（包括 target）都是正整数。
解集不能包含重复的组合。 
示例 1:

输入: candidates = [2,3,6,7], target = 7,
所求解集为:
[
  [7],
  [2,2,3]
]
示例 2:

输入: candidates = [2,3,5], target = 8,
所求解集为:
[
  [2,2,2,2],
  [2,3,3],
  [3,5]
]

**分析：**

使用回溯法求解
详细可参考https://blog.csdn.net/mmchinamm/article/details/52312064。

**解答：**

````java
package net.jerryfu.leetCodeMedium;

import java.util.ArrayList;
import java.util.List;
import org.junit.Test;

public class _039CombinationSum {

	public List<List<Integer>> combinationSum(int[] candidates, int target) {
		List<List<Integer>> resultList=new ArrayList<List<Integer>>();
		List<Integer> subList=new ArrayList<>();
		if (candidates==null) {
			return resultList;
		}
		doCombination(candidates,target,0,candidates.length-1,resultList,subList);
		return resultList;
	}
	
	private void doCombination(int[] candidates, int target, int low, int high, List<List<Integer>> resultList,
			List<Integer> subList) {
		if (candidates==null) {
			return;
		}
		if (target==0) {
			if (subList.size()==0) {
				return;
			}
			List<Integer> tempSublist=new ArrayList<>();
			for (Integer subListItem : subList) {
				tempSublist.add(subListItem);
			}
			resultList.add(tempSublist);
			return;
		}
		if (low>high) {
			return;
		}
		if (target<0) {
			return;
		}
		subList.add(candidates[low]);
		//先一直加最左边的元素
		doCombination(candidates, target-candidates[low], low, high, resultList, subList);
		//回退一个元素
		subList.remove(subList.size()-1);
		//最左点右移
		doCombination(candidates, target, low+1, high, resultList, subList);
	}

	@Test
	public void test() {
		int[] candidates=new int[]{2,3,5};
		int target=8;
		List<List<Integer>> combinationSum = combinationSum(candidates, target);
		for (List<Integer> list : combinationSum) {
			System.out.println(list);
		}
	}

}
````

