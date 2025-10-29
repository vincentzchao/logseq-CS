tags:: [[Dart]]
---

- ## Special-support types
	- Dart 对如下类型有特殊支持:
		- [[Dart Syntax/Numbers]]
		  logseq.order-list-type:: number
		- [[Dart Syntax/Strings]]
		  logseq.order-list-type:: number
		- [[Dart Syntax/Booleans]]
		  logseq.order-list-type:: number
		- [[Dart Syntax/Records]]
		  logseq.order-list-type:: number
		- [[Dart Syntax/Functions]]
		  logseq.order-list-type:: number
		- [[Dart Syntax/Lists]]
		  logseq.order-list-type:: number
		- [[Dart Syntax/Sets]]
		  logseq.order-list-type:: number
		- [[Dart Syntax/Maps]]
		  logseq.order-list-type:: number
		- [[Dart Syntax/Runes]]
		  logseq.order-list-type:: number
		- [[Dart Syntax/Symbols]]
		  logseq.order-list-type:: number
		- [[Dart Syntax/Null Type]] (注意这是一个类)
		  logseq.order-list-type:: number
	- 以上类都可以使用 **字面量 (literal)** 去创建对象.
- ## Special-role types
	- Dart 中的如下类型 , 有特殊作用:
		- [[Dart Syntax/Object Type]] : 是除了 `NUll` 之外的所有 `class` 的 `superclass` .
		  logseq.order-list-type:: number
		- [[Dary Syntax/Enum Type]] : 是所有 **枚举类** 的 `superclass` .
		  logseq.order-list-type:: number
		- `Future` and `Stream`: 用于 [[Dart Syntax/Async]]
		  logseq.order-list-type:: number
		- [[Dart Syntax/Iterable Type]] :  由于 `for-in loops` 和 `synchronous generator functions` 中.
		  logseq.order-list-type:: number
		- [[Dart Syntax/Never Type]] : 表示表达式永远无法成功完成求值.
		  logseq.order-list-type:: number
		- [[Dart Syntax/dynamic Type]] : 表示禁用 `Static Checking` , 不过通常应该改用 `Object` / `Object?` .
		  logseq.order-list-type:: number
		- `void` : 表示某个值永远不会被使用, 常用作 **返回类型** .
		  logseq.order-list-type:: number
- ## Special-in-class-hierarchy types
	- Dart 中的如下类型, 在 `class` 的继承关系中, 有特殊作用:
		- `Object`
		  logseq.order-list-type:: number
		- `Object?`
		  logseq.order-list-type:: number
		- [[Dart Syntax/Null Type]]
		  logseq.order-list-type:: number
		- [[Dart Syntax/Never Type]]
		  logseq.order-list-type:: number
- ## 参考
	- [Dart Docs - Built-in types](https://dart.dev/language/built-in-types)
	  logseq.order-list-type:: number
	-