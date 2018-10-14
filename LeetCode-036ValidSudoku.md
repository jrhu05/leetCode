---
title: LeetCode刷题笔记-036ValidSudoku
date: 2018-05-16 09:00:37
categories: 算法寻径
tags: [LeetCode]
---
**题目：**

判断一个 9x9 的数独是否有效。只需要根据以下规则，验证已经填入的数字是否有效即可。

数字 1-9 在每一行只能出现一次。
数字 1-9 在每一列只能出现一次。
数字 1-9 在每一个以粗实线分隔的 3x3 宫内只能出现一次。

数独部分空格内已填入了数字，空白格用 '.' 表示。

示例 1:

输入:
[
  ["5","3",".",".","7",".",".",".","."],
  ["6",".",".","1","9","5",".",".","."],
  [".","9","8",".",".",".",".","6","."],
  ["8",".",".",".","6",".",".",".","3"],
  ["4",".",".","8",".","3",".",".","1"],
  ["7",".",".",".","2",".",".",".","6"],
  [".","6",".",".",".",".","2","8","."],
  [".",".",".","4","1","9",".",".","5"],
  [".",".",".",".","8",".",".","7","9"]
]
输出: true
示例 2:

输入:
[
  ["8","3",".",".","7",".",".",".","."],
  ["6",".",".","1","9","5",".",".","."],
  [".","9","8",".",".",".",".","6","."],
  ["8",".",".",".","6",".",".",".","3"],
  ["4",".",".","8",".","3",".",".","1"],
  ["7",".",".",".","2",".",".",".","6"],
  [".","6",".",".",".",".","2","8","."],
  [".",".",".","4","1","9",".",".","5"],
  [".",".",".",".","8",".",".","7","9"]
]
输出: false
解释: 除了第一行的第一个数字从 5 改为 8 以外，空格内其他数字均与 示例1 相同。
​     但由于位于左上角的 3x3 宫内有两个 8 存在, 因此这个数独是无效的。
说明:

一个有效的数独（部分已被填充）不一定是可解的。
只需要根据以上规则，验证已经填入的数字是否有效即可。
给定数独序列只包含数字 1-9 和字符 '.' 。
给定数独永远是 9x9 形式的。

**分析：**

行和列的检查都很简单，对3x3宫内的检查稍微麻烦点。

**解答：**

````java
package net.jerryfu.leetCodeMedium;

import java.util.HashMap;
import java.util.Map;
import org.junit.Test;

public class _036ValidSudoku {

	public boolean isValidSudoku(char[][] board) {
		
		if (!rowCheck(board)) {
			return false;
		}
		
		if (!colCheck(board)) {
			return false;
		}
		
		if(!cubeCheck(board)) {
			return false;
		}
		
	    return true;
	}

	private boolean rowCheck(char[][] board) {
		//判断行
		for (int i = 0; i < board.length; i++) {
			Map<Character, Integer> checkMap=intCheckMap();
			for (int j = 0; j < board.length; j++) {
				if (board[i][j]>='0'&&board[i][j]<='9') {
					//数量多于1个
					if (checkMap.get(board[i][j])>0) {
						return false;
					}else {
						checkMap.replace(board[i][j], 1);
					}
				}else if (board[i][j]!='.') {
					return false;
				}
			}
		}
		return true;
	}

	private boolean colCheck(char[][] board) {
		//判断列
		for (int i = 0; i < board.length; i++) {
			Map<Character, Integer> checkMap=intCheckMap();
			for (int j = 0; j < board.length; j++) {
				if (board[j][i]>='0'&&board[j][i]<='9') {
					//数量多于1个
					if (checkMap.get(board[j][i])>0) {
						return false;
					}else {
						checkMap.replace(board[j][i], 1);
					}
				}else if (board[j][i]!='.') {
					return false;
				}
			}
		}
		return true;
	}
	


	private boolean cubeCheck(char[][] board) {
		for (int i = 0; i < board.length; i+=3) {
			for (int j = 0; j < board.length; j+=3) {
				Map<Character, Integer> checkMap=intCheckMap();
				for (int iPlus = 0; iPlus < 3; iPlus++) {
					for (int jPlus = 0; jPlus < 3; jPlus++) {
						int iReal=i+iPlus;
						int jReal=j+jPlus;
						if (board[iReal][jReal]>='0'&&board[iReal][jReal]<='9') {
							//数量多于1个
							if (checkMap.get(board[iReal][jReal])>0) {
								return false;
							}else {
								checkMap.replace(board[iReal][jReal], 1);
							}
						}else if (board[iReal][jReal]!='.') {
							return false;
						}
					}
				}
			}
		}
		return true;
	}
	
	private Map<Character, Integer> intCheckMap() {
		// TODO Auto-generated method stub
		Map<Character, Integer> checkMap=new HashMap<>();
		for (char i='0';i<='9';i++) {
			checkMap.put(i, 0);
		}
		return checkMap;
	}

	/**
	 *["5","3",".",".","7",".",".",".","."],
	  ["6",".",".","1","9","5",".",".","."],
	  [".","9","8",".",".",".",".","6","."],
	  ["8",".",".",".","6",".",".",".","3"],
	  ["4",".",".","8",".","3",".",".","1"],
	  ["7",".",".",".","2",".",".",".","6"],
	  [".","6",".",".",".",".","2","8","."],
	  [".",".",".","4","1","9",".",".","5"],
	  [".",".",".",".","8",".",".","7","9"]
	 */
	@Test
	public void test() {
		char[][] board=new char[][] {
			{'5','3','.','.','7','.','.','.','.'},
			{'6','.','.','1','9','5','.','.','.'},
			{'.','9','8','.','.','.','.','6','.'},
			{'8','.','.','.','6','.','.','.','3'},
			{'4','.','.','8','.','3','.','.','1'},
			{'7','.','.','.','2','.','.','.','6'},
			{'.','6','.','.','.','.','2','8','.'},
			{'.','.','.','4','1','9','.','.','5'},
			{'.','.','.','.','8','.','.','7','9'}
			};
		System.out.println(isValidSudoku(board));
	}

}


````

