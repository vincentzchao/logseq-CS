tags:: [[Dart]]
---

- 类中可以定义对象的加减乘除等操作符的运算.
- 标识符以 `_` 开头的成员, 是 `private` 的.
- ## Type test operators
  id:: 68ff7a45-d7e4-4ba1-9e8b-d109ae29b84c
	- 参考: [Type test operators](https://dart.dev/language/operators#type-test-operators)
	  id:: 6900bfad-e0d3-474f-a030-fe3ffa43d5f6
	- ### Type Check
		- `is` :
			- 若对象为 `null` , 则返回 `false` .
			  logseq.order-list-type:: number
			- 若对象不为 `null` :
			  logseq.order-list-type:: number
				- 属于指定 `type` , 则返回 `true` , 
				  logseq.order-list-type:: number
				- 不属于指定 `type` , 则返回 `false` ,
				  logseq.order-list-type:: number
		- `is!` :
			- 若对象为 `null` , 则返回 `true` .
			  logseq.order-list-type:: number
			- 若对象不为 `null` :
			  logseq.order-list-type:: number
				- 属于指定 `type` , 则返回 `false` ,
				  logseq.order-list-type:: number
				- 不属于指定 `type` , 则返回 `true` ,
				  logseq.order-list-type:: number
			- ``` dart
			  Object a = 1;
			  print(a is int); // true
			  print(a is Object); // true
			  
			  print(a is! int); // false
			  print(a is! String); // true
			  
			  int? b = null;
			  print(b is int); // false
			  print(b is! int); // true
			  ```
	- ### Typecast
		- `as` : 将对象强转为指定类型 (如果值为 `null` , 或者不是指定类型, 则会抛出异常).
			- ``` dart
			  (employee as Person).firstName = 'Bob';
			  ```
		- 或者, 也可以使用 `is` 来处理:
			- ``` dart
			  if (employee is Person) {
			    // 类型检查通过之后, 可以直接访问 Person 类型的属性
			    employee.firstName = 'Bob';
			  }
			  ```
- ## Cascade notation
	- 参考: [Cascade notation](https://dart.dev/language/operators#cascade-notation)
	- 可以在对象后面接 **级联符号** `..` , 用来连续多次访问这个对象的属性和方法.
		- 在这过程中的返回值会被忽略, 最终返回这个对象本身.
		- ``` dart
		  StringBuffer sb = StringBuffer();
		  print(
		    sb
		    ..write('foo')
		    ..write('bar'),
		  ); // foobar
		  ```
	- 如果对象可能为 `null` , 可以将第一个使用 `..` 改为 `?..` .
		- 使用 `?..` 的效果是: 如果对象是 `null` , 则后续所有的级联操作都不会执行, 并最终返回 `null` (也即这个对象本身).
		- ``` dart
		  StringBuffer? sb = StringBuffer();
		  sb = null;
		  print(
		    sb
		    ?..write('foo')
		    ..write('bar'),
		  ); // null
		  ```
- ## Member access operators
	- 参考: [Other operators](https://dart.dev/language/operators#other-operators)
	- `.` : 成员访问 ( 对象不允许为 `null` )
	- `?.` : 条件成员访问 ( 对象允许为 `null` )
		- 如果对象为 `null` , 则表达式返回 `null` .
	- ``` dart
	  foo.bar;
	  foo?.bar  
	  ```
	-