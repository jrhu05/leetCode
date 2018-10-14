---
title: LeetCode刷题笔记-006ZigzagConversion
date: 2018-04-09 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

将字符串 "PAYPALISHIRING" 以Z字形排列成给定的行数：

P    A    H   N
A P L S I  I  G
Y     I    R
之后从左往右，逐行读取字符："PAHNAPLSIIGYIR"

实现一个将字符串进行指定行数变换的函数:

string convert(string s, int numRows);
示例 1:

输入: s = "PAYPALISHIRING", numRows = 3
输出: "PAHNAPLSIIGYIR"
示例 2:

输入: s = "PAYPALISHIRING", numRows = 4
输出: "PINALSIGYAHRPI"
解释:

P       I         N
A   L S      I  G
Y A   H R
P       I

**分析**

找规律：假设当前行数是r，总行数R，I(n)表示某行第n个字母在原字符串中的index，n从0开始：

r=1,R时，I(n+1) = I(n)+2(R-1)

1<r<R时，

I(n+1) = I(n)+2(R-r) n为偶数时，

I(n+1) = I(n)+2(r-1) n为奇数 

**解答：**

````java
import org.junit.Test;
public class _006ZigzagConversion {
	@Test
	public void test() {
		System.out.println(convert("PAYPALISHIRING", 3));
		System.out.println(convert("PAYPALISHIRING", 4));
	}
	public String convert(String s, int numRows) {
		if(s==null||s.length()==0||numRows==1||numRows>=s.length()) {  
            return s;  
        }  
        StringBuilder sb = new StringBuilder();  
          
        for(int i=1;i<s.length()+1;i+=2*(numRows-1)) {  
            sb.append(s.charAt(i-1));  
        }  
        for(int i=2;i<numRows;i++) {  
            boolean k = true;  
            for(int j=i;j<s.length()+1;j+=(k)?2*(numRows-i):2*(i-1),k=!k) {  
                sb.append(s.charAt(j-1));  
            }  
        }  
        for(int i=numRows;i<s.length()+1;i+=2*(numRows-1)) {  
            sb.append(s.charAt(i-1));  
        }  
        return sb.toString();  
    }
}

````









