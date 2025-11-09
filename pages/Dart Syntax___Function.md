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
	- ### Parameter types
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
	-
- ## Functions are objects
	- Dart 是一种真正的面向对象语言: 函数也是对象, 函数对象有其类型 (type) .
- ## Function Type
	- `Function` 类型, 是 **函数类型** 的 超类.
	- 所有实现了 `Function` 的对象, 都有超类为 `Function` 的函数类型.
	- `Function` 类型, 其本身不包含任何值.
- ## 参考
	- [Dart API - Function](https://api.dart.dev/dart-core/Function-class.html)
	  logseq.order-list-type:: number
	- [Dart Docs - Functions](https://dart.dev/language/functions)
	  logseq.order-list-type:: number