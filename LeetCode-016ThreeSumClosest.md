---
title: LeetCode刷题笔记-016ThreeSumClosest
date: 2018-04-19 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

给定一个包括 n 个整数的数组 nums 和 一个目标值 target。

找出 nums 中的三个整数，使得它们的和与 target 最接近。返回这三个数的和。假定每组输入只存在唯一答案。
例如，给定数组 nums = [-1，2，1，-4], 和 target = 1.
与 target 最接近的三个数的和为 2. (-1 + 2 + 1 = 2).

**分析**

基本的解法与逻辑和第15题很相似，也是确定一个被加数后，其余两个被加数向中心移动，移动的规则也是根据三数和与一固定值（target）的比较结果来确定。不同点是题15需要存储多组可能的结果，而本题只需要关注累加的和，反而简单了些许。

**解答：**

````java
package net.jerryfu.leetCodeMedium;

import java.util.Arrays;

import org.junit.Test;

public class _016ThreeSumClosest {
	@Test
	public void test() {
		int[] nums=new int[]{-1,2,1,-4};
		System.out.println(threeSumClosest(nums, 1));
	}
    public int threeSumClosest(int[] nums, int target) {
    	 //对数组进行排序
        Arrays.sort(nums);
        int closestSum = 0;
        int diff = Integer.MAX_VALUE;
        
        // 遍历数组
        for(int i=0; i<nums.length-2; i++)
        {
            int left = i + 1;
            int right = nums.length - 1;
            // 确定了i点，左右两点向内收缩
            while(left < right)
            {
                int temp_sum = nums[i] + nums[left] + nums[right];
                int temp_diff = Math.abs(temp_sum - target);
                //如果找到了更接近target的和则更新最接近的和以及差值
                if(temp_diff < diff)
                {
                    closestSum = temp_sum;
                    diff = temp_diff;
                }
                if(temp_sum < target) //temp_sum小于目标值则说明需要更大的被加数，所以左指针右移
                    left++;
                else if(temp_sum > target) //temp_sum大于目标值则说明需要更小的被加数，故右指针左移
                    right--;
                else
                    return temp_sum;
            }
        }
        return closestSum;
    }

}

````
