tags:: [[Character Set]]
---

- ## Unicode 的编码方式
	- Unicode 有如下编码方式:
		- [[UTF-32]] : 定长编码 32 位, 直接将码点 (十进制数) , 转为二进制比特位 .
		  logseq.order-list-type:: number
		- [[UTF-16]] : 不定长编码, 一个字符可能是 16 位 或 32 位.
		  logseq.order-list-type:: number
		- [[UTF-8]] : 不定长编码, 一个字符可能需要 8 位, 16 位 , 24 位 或 32 位.
		  logseq.order-list-type:: number
- ## 概念
	- `码点 Code Point` : Unicode 中字符的编号.
	- `代码单元 Code Unit` : Unicode 字符编码中, 表示字符的单元 (一个字符可以用 1 个或 多个 代码单元表示) .
		- [[UTF-8]] 中, 代码单元是 1 个字节.
		  logseq.order-list-type:: number
		- [[UTF-16]] 中, 代码单元是 2 个字节.
		  logseq.order-list-type:: number
		- [[UTF-32]] 中, 代码单元是 4 个字节.
		  logseq.order-list-type:: number
-