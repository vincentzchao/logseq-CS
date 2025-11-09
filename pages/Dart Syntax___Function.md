tags:: [[Dart]]
---

- ## Define a function
	- ``` dart
	  bool isNoble(int atomicNumber) {
	    return _nobleGases[atomicNumber] != null;
	  }
	  
	  // 虽然参数类型和返回值类型可以被推断出来, 但不建议省略
	  isNoble(atomicNumber) {
	    return _nobleGases[atomicNumber] != null;
	  }
	  ```
	- 声明 返回值, 函数名, 参数列表.
- ## Function Body
	- 函数体, 使用 `{}` 包裹.
	- 当函数体中只有一个表达式时, 可以使用 `=> expr` 语法来替代, 这被称为 **Arrow syntax (箭头语法)** .
		- ``` dart
		  bool isNoble(int atomicNumber) => _nobleGases[atomicNumber] != null;
		  ```
- ## Function Parameters
	- ### Parameter 分类
		- 函数的参数类型分为如下几类:
			- `Required positional parameters` (调用时, 必须按顺序传递的参数, 不能传参数名)
			  logseq.order-list-type:: number
			- `Named parameters` (调用时, 参数名和参数值一起传入的参数)
			  logseq.order-list-type:: number
			- `Optional positional parameters`
			  logseq.order-list-type:: number
		- 一个函数中可以有的参数类型和顺序是:
			- `Required positional parameters` , `Named parameters` 
			  logseq.order-list-type:: number
			- `Required positional parameters` , `Optional positional parameters`
			  logseq.order-list-type:: number
			- `Named parameters`
			  logseq.order-list-type:: number
			- `Optional positional parameters`
			  logseq.order-list-type:: number
		- 总结就是:
			- `Named parameters` 和 `Optional positional parameters` 不能同时出现.
			  logseq.order-list-type:: number
			- 如果有 `Required positional parameters` , 则必须放在 `Named parameters` 或 `Optional positional parameters` 的前面.
			  logseq.order-list-type:: number
	- ### Required positional parameters
		- 就咱们常见的参数类型.
		- 声明时, 不能用 `required` 修饰, 且不能给 **默认值** .
		- ``` dart
		  bool foo(int a, int b) {}
		  
		  foo(1, 2)
		  ```
		- 其特征是:
			- 调用时, 每个参数是必传.
			  logseq.order-list-type:: number
			- 调用时, 需按顺序传参.
			  logseq.order-list-type:: number
			- 调用时, 不能传参数名.
			  logseq.order-list-type:: number
	- ### Named parameters
		- 使用 `{}` 包裹起来的参数列表 : `{param1, param2, …}` .
		- ``` dart
		  void enableFlags({bool? bold, bool? hidden}) {
		  }
		  
		  // 调用
		  enableFlags(bold: true, hidden: false);
		  ```
		- 其特征是:
			- 调用时, 需要传入参数名与参数值对.
			  logseq.order-list-type:: number
			- 如果没用 `required` 修饰, 则是可选的 (optional) , 即 调用时 可以不传.
			  logseq.order-list-type:: number
				- 此时, 由于参数可选, 则必须保证其有值.
				- 所以, 要么定义为 `Nullable` 参数, 要么是给它设置一个默认值 (必须是 **编译时常量** ).
				- ``` dart
				  void enableFlags({bool? bold, bool hidden = true}) {
				  }
				  ```
			- 如果用了 `required` 修饰, 则是必需的 , 即 调用时 必传.
			  logseq.order-list-type:: number
				- ``` dart
				  void enableFlags({required bool bold, bool hidden = true}) {
				  }
				  ```
				- 定义为 required 的参数, 也可以是 Nullable 变量, 其值可以为 `null`
				- ``` dart
				  void enableFlags({required bool? bold, bool hidden = true}) {
				  }
				  ```
			- 调用时, Named parameters 可以按任意顺序传参.
			  logseq.order-list-type:: number
				- 但 Required positional parameters 整体, 还是要按顺序传参.
				- ``` dart
				  void foo(int a, int b, {bool c = true, bool? d}) {
				    print('hello $a $b $c $d');
				  }
				  
				  foo(c: false, d: true, 1, 2);
				  ```
	- ### Optional positional parameters
		- 使用 `[]` 包裹起来的参数 : `[param1, param2, …]` .
		- ``` dart
		  String say(String from, String msg, [String? device]) {
		    var result = '$from says $msg';
		    if (device != null) {
		      result = '$result with a $device';
		    }
		    return result;
		  }
		  
		  say('Bob', 'Howdy') 
		  ```
		- 其特征是:
			- 调用时, `[]` 中的参数可以不传.
			  logseq.order-list-type:: number
				- 此时, 由于参数可选, 则必须保证其有值.
				- 所以, 要么定义为 `Nullable` 参数, 要么是给它设置一个默认值 (必须是 **编译时常量** ).
				- ``` dart
				  void bar(int a, int b, [bool c = true, bool? d]) {
				    print('hello $a $b $c $d');
				  }
				  ```
			- 调用时, 不能指定参数名.
			  logseq.order-list-type:: number
			- 调用时, 如果需要传入多个 **Optional positional parameters** , 则必须按顺序从左外右传入, 且不能跳过中间的可选参数.
			  logseq.order-list-type:: number
				- ``` dart
				  void bar(int a, int b, [bool c = true, bool? d]) {
				    print('hello $a $b $c $d');
				  }
				  
				  bar(1, 2, false);
				  ```
	- ### Trailing commas
		- 定义函数的参数列表, 和 调用函数时传参 , 都可以使用 末尾逗号 (Trailing comma) .
			- ==但其实格式化时会被去掉==
		- ``` dart
		  void foo(int a, int b, int c,) {}
		  
		  foo(1, 2, 3,);
		  ```
- ## The main() function
	- 每个 Dart 应用, 都必须要有一个 `Top-level` 的  `main()` 方法, 它是 Dart 应用的入口.
		- ``` dart
		  void main() {
		    print('Hello, World!');
		  }
		  ```
	- `main()` 方法的返回值类型为 `void` .
	- `main()` 方法可以使用 `List<String>` 参数, 接受来自命令行的参数.
		- ``` dart
		  void main(List<String> arguments) {
		    print(arguments);
		  
		    assert(arguments.length == 2);
		    assert(int.parse(arguments[0]) == 1);
		    assert(arguments[1] == 'test');
		  }
		  ```
	- ==可以使用 [args](https://pub.dev/packages/args) 库来处理命令行参数. ==
- ## Anonymous functions
	- ### Anonymous function syntax
		- 声明时, 没有名称的函数, 被称为 `anonymous functions` , 或 `lambdas` / `closures` .
		- ``` dart
		  ([[Type] param1[, ...]]) {
		    codeBlock;
		  }
		  ```
		- 参数列表可以带类型, 也可以不带类型.
	- ### Anonymous function as a parameter
		- ``` dart
		  const list = ['apples', 'bananas', 'oranges'];
		  
		  var uppercaseList = list.map((item) {
		    return item.toUpperCase();
		  }).toList();
		  // Convert to list after mapping
		  
		  for (var item in uppercaseList) {
		    print('$item: ${item.length}');
		  }
		  ```
		- 其中的如下代码就属于匿名函数:
			- ``` dart
			  (item) {
			    return item.toUpperCase();
			  }
			  ```
	- ### Anonymous function as a variable
		- 也可以将 **匿名函数** 赋值给一个变量.
		- ``` dart
		  var upper = (item) {
		    return item.toUpperCase();
		  };
		  print(upper("abc"));
		  ```
- ## Lexical scope
	- Lexical scope 即 词法作用域, Dart 根据变量的位置, 确定其作用域 (scope) .
	- `{}` 内的变量, 只在 `{}` 内有效 (也在 `{}` 内的 `{}` 内有效):
		- ``` dart
		  bool topLevel = true;
		  
		  void main() {
		    var insideMain = true;
		  
		    void myFunction() {
		      var insideFunction = true;
		  
		      void nestedFunction() {
		        var insideNestedFunction = true;
		  
		        assert(topLevel);
		        assert(insideMain);
		        assert(insideFunction);
		        assert(insideNestedFunction);
		      }
		    }
		  }
		  ```
- ## Function Type
	- ### Functions as first-class objects
		- Dart 是一种真正的面向对象语言: 函数也是对象, 函数对象有其类型 (type) .
		- 函数是 **一等对象 ( [[First-class]] object)** (即 和其它对象一样, 享有相同的权利)
			- 可以作为参数传递:
			  logseq.order-list-type:: number
				- ``` dart
				  void printElement(int element) {
				    print(element);
				  }
				  
				  var list = [1, 2, 3];
				  
				  // Pass printElement as a parameter.
				  list.forEach(printElement);
				  ```
			- 可以被赋值给变量:
			  logseq.order-list-type:: number
				- ``` dart
				    void foo() {
				      print('hello');
				    }
				  
				    var bar = foo;
				    bar();
				  ```
			- 可以作为返回值被其他函数返回
			  logseq.order-list-type:: number
	- ### Specify Function Type
		- ``` dart
		  void greet(String name, {String greeting = 'Hello'}) => print('$greeting $name!');
		  
		  // Store `greet` in a variable and call it.
		  void Function(String, {String greeting}) g = greet;
		  g('Dash', greeting: 'Howdy');
		  ```
		- 将 **函数声明头 (function declaration header)** 的 **函数名** , 换成 `Function` 关键字, 并将 **默认值** 去掉, 就是 **Function Type** .
		- **Positional parameters** ( **Required positional parameters** 和 **Optional positional parameters** ) 的 参数名称可以省略, **Names parameters** 不可省略参数名.
	- ### Function class
		- 所有的 **函数对象** , 都有其所属的 **函数类型**  .
		- `Function` 类型, 是所有 **函数类型** 的超类.
			- `Function` 类型, 其本身不包含任何值.
- ## 参考
	- [Dart API - Function](https://api.dart.dev/dart-core/Function-class.html)
	  logseq.order-list-type:: number
	- [Dart Docs - Functions](https://dart.dev/language/functions)
	  logseq.order-list-type:: number