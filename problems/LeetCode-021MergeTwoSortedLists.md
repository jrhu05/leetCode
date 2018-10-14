---
title: LeetCode刷题笔记-021MergeTwoSortedLists
date: 2018-02-27 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

合并两个已排序的链表，并将其作为一个新列表返回。新列表应该通过拼接前两个列表的节点来完成。 

示例：

输入：1->2->4, 1->3->4
输出：1->1->2->3->4->4

**分析**

双指针，两序列长之和，注意特殊情况的处理

**解答：**

````java
import org.junit.Test;
public class _021MergeTwoSortedLists {
	
	@Test
	public void test() {
		ListNode l1=new ListNode(1);
		l1.next=new ListNode(2);
		l1.next.next=new ListNode(4);
		ListNode l2=new ListNode(1);
		l2.next=new ListNode(3);
		l2.next.next=new ListNode(4);
		l2.next.next.next=new ListNode(5);
		l2.next.next.next.next=new ListNode(6);
		ListNode result=mergeTwoLists(l1, l2);
		while (result.next!=null) {
			System.out.print(result.val+"-->");
			result=result.next;
		}
		System.out.println(result.val);
	}
	
	public ListNode mergeTwoLists(ListNode l1, ListNode l2) {
		
		 if(l1 == null && l2 == null)
	            return null;
	        if(l1 == null)
	        {
	            return l2;
	        }

	        if(l2 == null){
	            return l1;
	        }
		
		ListNode temp1=l1;
		ListNode temp2=l2;
		int len1=1;
		while (temp1.next!=null) {
			len1++;
			temp1=temp1.next;
		}
		int len2=1;
		while (temp2.next!=null) {
			len2++;
			temp2=temp2.next;
		}
		int totalLen=len1+len2;
		ListNode head= new ListNode(0);
		ListNode result=head;

		for (int i = 0; i < totalLen; i++) {
			if (l1==null&&l2!=null) {
				head.next=l2;
				head=l2;
				l2=l2.next;
				continue;
			}
			if (l1!=null&&l2==null) {
				head.next=l1;
				head=l1;
				l1=l1.next;
				continue;
			}
			if (l1.val<l2.val) {
				head.next=l1;
				head=l1;
				l1=l1.next;
			}else {
				head.next=l2;
				head=l2;
				l2=l2.next;
			}
		}
		
		return result.next;
     }
}

````









