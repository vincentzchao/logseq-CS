tags:: [[Dart]]
---

- ## UTF-16
	- Dart 的 `String` 对象, 使用 [[UTF-16]] 编码.
	- 存储时按照 UTF-16 code units 进行存储.
- ## Single or Double quotes
	- ``` dart
	  var s1 = 'Single quotes work well for string literals.';
	  var s2 = "Double quotes work just as well.";
	  var s3 = 'It\'s easy to escape the string delimiter.';
	  var s4 = "It's even easier to use the other delimiter.";
	  ```
	- 字符串字面量, 使用 `单引号` 和 `双引号` 都可以.
	- 可以使用 `\` 进行 [[转义]] .
- ## String interpolation (字符串插值)
	- ``` dart
	  var s = 'string interpolation';
	  print('Dart has $s, which is very handy.');
	  print('That deserves all caps. ${s.toUpperCase()} is very handy!')
	  ```
	- 使用 `${ expression }` 语法, 可以在字符串中插入表达式的值.
	  logseq.order-list-type:: number
	- 如果 表达式 是一个 **标识符 (identifier)** , 则可以省略 `{}` , Dart 会调用它的 `toString()` 方法.
	  logseq.order-list-type:: number
- ## String concatenation (字符串拼接)
	- **Adjacent string literals (相邻字符串字面量)** 语法
	  id:: 6904daf9-3910-4e95-bd3d-bafd535c3b0b
		- ``` dart
		  var s1 =
		      'String '
		      'concatenation'
		      " works even over line breaks.";
		  ```
	- 使用 `+` 运算符
		- ``` dart
		  var s2 = 'The + operator ' + 'works, as well.';
		  ```
- ## Multi-line string
	- ``` dart
	  var s1 = '''
	  You can create
	  multi-line strings like this one.
	  ''';
	  
	  var s2 = """This is also a
	  multi-line string.""";
	  ```
- ## Raw String
	- ``` dart
	  var s = r'In a raw string, not even \n gets special treatment.';
	  ```
	- 在字符串字面量前使用 `r` , 表示字符串中的 `\` 不是 [[转义]] 字符 , 是普通字符.
- ## Compile-time Constant
	- 如果一个字符串字面量中没有插值表达式, 则它必然是 **编译时常量 (Compile-time Constant) **
	- 如果一个字符串字面量中有插值表达式, 则:
		- 如果表达式的计算结果是值为 null / 数值 / 字符串 / 布尔值 的 **编译时常量** , 那么这个字符串也是 **编译时常量 (Compile-time Constant) **
-
- ## 参考
	- [Built-int types#strings](https://dart.dev/language/built-in-types#strings)
	  logseq.order-list-type:: number