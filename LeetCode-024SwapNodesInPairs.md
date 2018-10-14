---
title: LeetCode刷题笔记-024SwapNodesInPairs
date: 2018-05-01 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

给定一个链表，两两交换其中相邻的节点，并返回交换后的链表。

示例:

```
给定 1->2->3->4, 你应该返回 2->1->4->3.
```

说明:

- 你的算法只能使用常数的额外空间。
- **你不能只是单纯的改变节点内部的值**，而是需要实际的进行节点交换。

**分析**

由于要交换相邻两个节点的位置，则必须要维护与前一组已经交换位置的后一个节点的先后顺序，那么我们可以维护一个总是指向需要调换位置的两个节点的前一个节点的指针来进行相关的操作。

**解答：**

````java
package net.jerryfu.leetCodeMedium;

import org.junit.Test;
import net.jerryfu.support.ListNode;
public class _024SwapNodesInPairs {

	 public ListNode swapPairs(ListNode head) {
		 if (head==null) {
			return head;
		}
		 	ListNode result=head.next;
		 	if (head.next==null) {
				return head;
			}
		 	ListNode ft=new ListNode(999);
		 	ft.next=head;
		 	while (ft.next!=null&&ft.next.next!=null) {
		 		System.out.println(ft.val+"->"+ft.next.val);
				ListNode temp=ft.next.next;
				ft.next.next=ft.next.next.next;
				temp.next=ft.next;
				ft.next=temp;
				if (ft.next.next!=null) {
					ft=ft.next.next;
				}else {
					return result;
				}
			}
		 	return result;
	    }
	
	@Test
	public void test() {
		ListNode l6=new ListNode(6);
		ListNode l5=new ListNode(5);
		ListNode l4=new ListNode(4);
		ListNode l3=new ListNode(3);
		ListNode l2=new ListNode(2);
		ListNode l1=new ListNode(1);
		
		l1.next=l2;
		l2.next=l3;
		l3.next=l4;
		l4.next=l5;
		l5.next=l6;
		
		ListNode removeNthFromEnd = swapPairs(l1);
		
		printList(removeNthFromEnd);
	}
	
	private void printList(ListNode removeNthFromEnd) {
		// TODO Auto-generated method stub
		while (removeNthFromEnd.next!=null) {
			System.out.println(removeNthFromEnd.val);
			removeNthFromEnd=removeNthFromEnd.next;
		}
		System.out.println(removeNthFromEnd.val);
	}

}

````
