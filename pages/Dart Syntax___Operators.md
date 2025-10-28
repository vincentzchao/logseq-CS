tags:: [[Dart]]
---

- ## Overview
	- ![image.png](../assets/image_1761494169335_0.png){:height 723, :width 671}
	- [图源](https://dart.dev/language/operators)
	- 表中运算符的优先级, 从上往下是递减的 (即位置越高的操作符, 其优先级越高, 计算时先计算)
		- **Associativity** 的含义参见: [[Operator Associativity]]
- ## Arithmetic Operators
	- ### 加减乘除
		- `+` : 加
		- `-` : 减/负号
		- `*` : 乘
		- `%` : 取模 (即 获取证书除法的余数)
		- ==除法需要注意:==
			- `/` : 除法 (结果取确切值)
			- `~/` : 除法 (结果取整)
			- ``` dart
			    print(7 / 2); // 3.5
			    print(7 ~/ 2); // 3
			  ```
	- ### 自增&自减
		- `++var` 等价于 `var = var + 1` ,  表达式的值是 `var + 1`
		  logseq.order-list-type:: number
		- `var++` 等价于 `var = var + 1` ,  表达式的值是 `var`
		  logseq.order-list-type:: number
		- `--var` 等价于 `var = var - 1` ,  表达式的值是 `var - 1`
		  logseq.order-list-type:: number
		- `var--` 等价于 `var = var - 1` ,  表达式的值是 `var` .
		  logseq.order-list-type:: number
- ## Equality and relational operators
	- `==` : Equal
		- 比较两个对象所表示的东西, 是否一致.
			- 如果要比较是否是同一个对象, 使用 `identical()` 函数 .
		- 其工作原理:
			- 如果两个都是 `null` , 则为 `true` ; 
			  logseq.order-list-type:: number
			- 如果其中只有一个是 `null` , 则为 `false` ;
			  logseq.order-list-type:: number
			- 如果都不是 `null` , 则调用左侧对象的 `==` 运算方法.
			  logseq.order-list-type:: number
	- `!=` : Not equal
	- `>` : Greater than
	- `<` : Less than
	- `>=` : Greater than or equal to
	- `<=` : Less than or equal to
- ## Type test operators
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
- ## Logical operators
	- `!` : 逻辑取反
	- `||` : 逻辑或
	- `&&` : 逻辑与
- ## Bitwise operators
	- `&` : 按位 与 运算.
	- `|` : 按位 或 运算.
	- `^` : 按位 [[异或]] 运算 (两个值不同时结果为 1, 相同时为 0).
	- `~` : 按位 取反 (一元操作符, 0 变 1, 1 变 0)
- ## Shift Operators
	- 参见 : [[Shift Left & Shift Right]]
	- `<<` : 左移 (Shift left)
	- `>>` : 右移 (Shift left)
	- `>>>` : 无符号右移 (Unsigned shift right)
- ## Assignment operators
	- ### Simole assignment operators
		- `=` : 赋值
		- `??=` : 左边的变量为 `null` 时, 才被赋值, 否则不做任何处理.
	- ### Compound assignment operators
		- `+=` , `-=` , `*=` ,  `/=` , `~/=` ,  `%=`
		- `&=` ,  `|=` , `^=`
		- `<<=` ,  `>>=` , `>>>=`
		- 对于 Compound assignment operators :
			- `a op= b` 等价于 `a = a op b`
			- 例如  `a += b` 等价于 `a = a + b` .
- ## Conditional expressions
	- ### Conditional operator
		- `condition ? expr1 : expr2`
			- `condition` 为 `true` , 则计算并返回 `expr1` 的值.
			- `condition` 为 `false` , 则计算并返回 `expr2` 的值.
	- ### If-null operator
		- `expr1 ?? expr2`
			- `expr1` 不为 null , 则返回 `expr1` 的值.
			- `expr1` 为 null , 则计算并返回 `expr2` 的值.
- ## Cascade notation
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
- ## Spread operators
	-
- ## 参考
	- [Dart Docs - Operators](https://dart.dev/language/operators)
	  logseq.order-list-type:: number
	-
-