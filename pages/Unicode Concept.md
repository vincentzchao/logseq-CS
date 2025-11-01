tags:: [[Unicode]]
---

- ## Unicode 是什么
	- Unicode 是一种字符集, 与具体的字符编码是有区别的.
		- 符集与字符编码的区别, 阅读: [[字符集与字符编码]]
- ## Unicode 的编码方式
	- Unicode 有如下编码方式:
		- [[UTF-32]] : 定长编码 32 位, 直接将码点 (十进制数) , 转为二进制比特位 .
		  logseq.order-list-type:: number
		- [[UTF-16]] : 不定长编码, 一个字符可能是 16 位 或 32 位.
		  logseq.order-list-type:: number
		- [[UTF-8]] : 不定长编码, 一个字符可能需要 8 位, 16 位 , 24 位 或 32 位.
		  logseq.order-list-type:: number
- ## Code Point 与 Code Unit
	- `码点 Code Point` : Unicode 中字符的编号.
	- `代码单元/码元 Code Unit` : Unicode 字符编码中, 表示字符的单元 (一个字符可以用 1 个或 多个 代码单元表示) .
		- [[UTF-8]] 中, 代码单元是 1 个字节.
		  logseq.order-list-type:: number
		- [[UTF-16]] 中, 代码单元是 2 个字节.
		  logseq.order-list-type:: number
		- [[UTF-32]] 中, 代码单元是 4 个字节.
		  logseq.order-list-type:: number
- ## Surrogate 代理项
	- Surrogate 是给 [[UTF-16]] 预留的码点, 不会被分配给任何字符.
		- [[UTF-16]] 为什么需要预留码点? 因为其编码规则的特殊性.
	- 一些 码点 比较大的字符, UTF-16 使用 2 个字节无法覆盖, 需要 2 个 Surrogate 组合而成 (共 4 个字节), 这被称为 **Surrogate pair (代理对)** .
		- 如 "Man" emoji 的 Unicode 字符（'👨'，U+1F468）, 由代理项 `U+D83D` 和 `U+DC68` 组合而成.
	- UTF-8 和 UTF-32 使用不到 Surrogate .
-