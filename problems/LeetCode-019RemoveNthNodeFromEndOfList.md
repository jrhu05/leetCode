---
title: LeetCode刷题笔记-019RemoveNthNodeFromEndOfList
date: 2018-04-25 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

给定一个链表，删除链表的倒数第 n 个节点，并且返回链表的头结点。

示例：

给定一个链表: 1->2->3->4->5, 和 n = 2.

当删除了倒数第二个节点后，链表变为 1->2->3->5.
说明：

给定的 n 保证是有效的。

进阶：

你能尝试使用一趟扫描实现吗？

**分析**

我只能想得到两次遍历的实现方式，一次统计列表长度，一次执行实际的删除操作。一趟扫描实现是不是使用双指针来进行？一个先走N步，另一个开始同步后移，第一个指针到尾巴的时候，第二个指针就正好指向了要删除的节点。

**解答：**

````java
package net.jerryfu.leetCodeMedium;

import org.junit.Test;
import net.jerryfu.support.ListNode;
public class _019RemoveNthNodeFromEndOfList {

	public ListNode removeNthFromEnd(ListNode head, int n) {
		ListNode temp=head;
		int count=0;
		while (temp.next!=null) {
			count++;
			temp=temp.next;
		}
		count++;
		int position=count-n;
		if (position==0) {
			return head.next;
		}
		temp=head;
		count=1;
		while (count<position) {
			temp=temp.next;
			count++;
		}
		temp.next=temp.next.next;

        return head;
    }
	
	@Test
	public void test() {
		ListNode l5=new ListNode(5);
		ListNode l4=new ListNode(4);
		ListNode l3=new ListNode(3);
		ListNode l2=new ListNode(2);
		ListNode l1=new ListNode(1);
		
		l1.next=l2;
		l2.next=l3;
		l3.next=l4;
		l4.next=l5;
		
		ListNode removeNthFromEnd = removeNthFromEnd(l1, 5);
		
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
