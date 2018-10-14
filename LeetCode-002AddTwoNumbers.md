---
title: LeetCode刷题笔记-002AddTwoNumbers
date: 2018-02-15 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

给定两个非空链表来代表两个非负整数，位数按照逆序方式存储，它们的每个节点只存储单个数字。将这两数相加会返回一个新的链表。

你可以假设除了数字 0 之外，这两个数字都不会以零开头。

示例：

输入：(2 -> 4 -> 3) + (5 -> 6 -> 4)
输出：7 -> 0 -> 8
原因：342 + 465 = 807

**分析**

先找出两个列表的长度最大值，然后逐个处理每个位的加法，注意好进位与端点的处理即可。

**解答：**

````java
import org.junit.Test;
public class _002AddTwoNumbers {
	/**
	 * /**
 * Definition for singly-linked list.
 * public class ListNode {
 *     int val;
 *     ListNode next;
 *     ListNode(int x) { val = x; }
 * }
 */
	
	@Test
	public void test() {
		ListNode l1=new ListNode(1);
		//l1.next=new ListNode(4);
		//l1.next.next=new ListNode(3);
		ListNode l2=new ListNode(9);
		l2.next=new ListNode(9);
		//l2.next.next=new ListNode(4);
		//l2.next.next.next=new ListNode(7);
		ListNode result=addTwoNumbers(l1, l2);
		while (result!=null) {
			System.out.println(result.val);
			result=result.next;
		}
	}
	
	public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
	       ListNode temp1=l1;
	       ListNode temp2=l2;
	       int length1=1;
	       int length2=1;
	       while (temp1.next!=null) {
	    	   length1++;
	    	   temp1=temp1.next;
	       }
	       while (temp2.next!=null) {
	    	   length2++;
	    	   temp2=temp2.next;
	       }
	       int length=length1>=length2?length1:length2;
	       int[] result=new int[length+1];
	      for (int i = 0; i < result.length; i++) {
			result[i]=0;
	      }
	      for (int i = 0; i < result.length; i++) {
	    	  //System.out.println("l1-->"+l1.val);
	    	  //System.out.println("l2-->"+l2.val);
	    	   int sum=0;
	    	  if (l1!=null&&l2!=null) {
				sum= l1.val+l2.val;
			}else if (l1==null&l2!=null) {
				sum=l2.val;
			}else if(l2==null&&l1!=null) {
				sum=l1.val;
			}
	    	  
	    	  result[i]=result[i]+sum;
	    	  boolean addFlag=false;
	    	  //System.out.println(sum);
	    	  if (result[i]>=10) {
	    		  result[i]=result[i]-10;
				addFlag=true;
			}
	    	  if (addFlag) {
				result[i+1]=1;
			}
	    	  if (l1!=null&&l1.next!=null) {
				l1=l1.next;
			}else {
				l1=null;
			}
	    	  if (l2!=null&&l2.next!=null) {
				l2=l2.next;
			}else {
				l2=null;
			}
	    	  
	      }
	      ListNode resultList=new ListNode(result[0]);
	      ListNode listHead=resultList;
	      int max=0;
	      if (result[result.length-1]==0) {
			max=result.length-1;
	      }else {
			max=result.length;
		}
	      for (int i = 1; i < max; i++) {
	    	  resultList.next=new ListNode(result[i]);
	    	  resultList=resultList.next;
	      }
	       return listHead;
	    }
}
````









