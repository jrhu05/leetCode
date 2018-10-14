---
title: LeetCode刷题笔记-011ContainerWithMostWater
date: 2018-04-13 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

给定 *n* 个非负整数 *a*1，*a*2，...，*a*n，每个数代表坐标中的一个点 (*i*, *ai*) 。画 *n* 条垂直线，使得垂直线 *i* 的两个端点分别为 (*i*, *ai*) 和 (*i*, 0)。找出其中的两条线，使得它们与 *x* 轴共同构成的容器可以容纳最多的水。

**注意：**你不能倾斜容器，*n* 至少是2。

**分析**

从两端先中间收缩，因为面积取决于第的一边高度和两边间距，一次高度较高的一边向内收缩只会导致总面积变小。故每次只需考虑移动高度较低的一边，直至两边相遇。

**解答：**

````java
import org.junit.Test;

public class _011ContainerWithMostWater {
	@Test
	public void test() {
		System.out.println(maxArea(new int[] {3,5,2,6,9,8}));
	}
	
	 public int maxArea(int[] height) {
        int left = 0;
        int right = height.length-1;
        int max = 0;
        while(left<right){
            max = Math.max(max, Math.min(height[left], height[right])*(right-left));
            if(height[left]<height[right]){
                left++;
            }else{
                right--;
            }
        }
        return max;
    }
	
}


````









