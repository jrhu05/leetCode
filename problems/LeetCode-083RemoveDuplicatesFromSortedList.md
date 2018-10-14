---
title: LeetCode刷题笔记-083RemoveDuplicatesFromSortedList
date: 2018-03-23 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

给定一个排序链表，删除所有重复的元素使得每个元素只留下一个。
案例：
给定 1->1->2，返回 1->2
给定 1->1->2->3->3，返回 1->2->3

**分析**

easy，略

**解答：**

````java
import org.junit.Test;
public class _083RemoveDuplicatesFromSortedList {
	@Test
	public void test() {
//		ListNode head=new ListNode(1);
//		head.next=new ListNode(1);
//		head.next.next=new ListNode(2);
//		ListNode result=deleteDuplicates(head);
//		while (result.next!=null) {
//			System.out.println(result.val);
//			result=result.next;
//		}
//		System.out.println(result.val);
//		System.out.println("=================");
		//给定 1->1->2->3->3，返回 1->2->3
		ListNode head2=new ListNode(1);
		head2.next=new ListNode(1);
		head2.next.next=new ListNode(2);
		head2.next.next.next=new ListNode(3);
		head2.next.next.next.next=new ListNode(3);
		 ListNode result=deleteDuplicates(head2);
		 System.out.println(result);
		while (result.next!=null) {
			System.out.println(result.val);
			result=result.next;
		}
		System.out.println(result.val);
		
//		ListNode head3=new ListNode(1);
//		head3.next=new ListNode(1);
//		head3.next.next=new ListNode(1);
//		ListNode result=deleteDuplicates(head3);
//		 System.out.println(result);
//		while (result.next!=null) {
//			System.out.println(result.val);
//			result=result.next;
//		}
//		System.out.println(result.val);
	}
	/**
	 * Definition for singly-linked list.
	 * public class ListNode {
	 *     int val;
	 *     ListNode next;
	 *     ListNode(int x) { val = x; }
	 * }
	 */
	 public ListNode deleteDuplicates(ListNode head) {
	        if (head==null) {
				return null;
			}
	        if (head.next==null) {
				return head;
			}
	        int temp=head.val;
	        ListNode result=head;
	        while (head!=null&&head.next!=null) {
				if (head.next.val==temp) {
					head.next=head.next.next;
				}else {
					temp=head.next.val;
					head=head.next;
				}
			}
	        return result;
	  }
}

````

