## Strict mode
	- 使用如下代码，可以在 Strict mode 下运行测试代码。
	- Strict mode 会对一些不好的语法特性做检查。
	- ``` js
	  (function(){
	  	"use strict"; 
	  	// 编写你的代码
	  })();
	  ```
- ## Comments
	- ### Line Comments
		- ``` js
		  // single line comment
		  ```
	- ### Block Comments
		- ``` js
		  /* This is a block comment */
		  
		  /* 
		   * this is a longer,
		   * multi-line comment
		   */
		  ```
		- Block Comments 中不能直接使用 `*/` ，需要进行转义，写为 `*\/` 。
		- ``` js
		  /* You can /* nest comments *\/ by escaping slashes */
		  ```
- ## Semicolons
	- 每条 Statement 后面的分号不是必须的。
	- MDN 建议的最佳实践是写分号，以尽可能减少出问题的机会。
		- > It is considered best practice, however, to always write a semicolon after a statement, even when it is not strictly needed. This practice reduces the chances of bugs getting into the code.
		  —— 引自 [MDN JavaScript Guide - Grammar and types](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Grammar_and_types#basics)
- ## Indentifiers
	- JS 的标识符 (即 变量、函数等的名称) 可以使用如下字符：
		- letter ( `a-z` 、 `A-Z` )
		  logseq.order-list-type:: number
		- underscore ( `_` )
		  logseq.order-list-type:: number
		- dollar sign ( `$` )
		  logseq.order-list-type:: number
		- numeric ( `0-9` )
		  logseq.order-list-type:: number
		- most Unicode letters (如 `å` and `ü` )
		  logseq.order-list-type:: number
	- 其中，只有 letter 、underscore 和 dollar sign 可以放在开头。
	- 另外，JS 大小写敏感。
- ## Variables
	- ### Declaration and initialization
		- ``` js
		  var name1 = "jack";
		  let name2 = "jack";
		  // 常量，不可再被赋值
		  const name3 = "jack";
		  ```
		- 其中 `let name2` 被称为 declaration , `= "jack"`  被称为 initialization 。
		- 变量在使用前必须声明，因为虽然在声明一个变量前，对其进行赋值是合法的，但是可能会出问题。
			- ``` js
			  // 合法
			  hello = "world";
			  console.log(hello);
			  ```
	- ### Variable Naming Rules
		- 参考: [MDN - An aside on variable naming rules](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps/Variables#an_aside_on_variable_naming_rules)
		- 建议只使用如下字符:
		  logseq.order-list-type:: number
			- Latin characters: `0-9` 、 `a-z` 、 `A-Z`
			  logseq.order-list-type:: number
			- Underscore character: `_`
			  logseq.order-list-type:: number
		- `0-9` 和 `_` 不能放在开头。
		  logseq.order-list-type:: number
		- 使用 `lower camel case` 。
		  logseq.order-list-type:: number
	- ### Variable scope
		- JS 中的变量有如下几种作用域：
			- Global scope: script mode 下的默认作用域。
			- Module scope: module mode 下的作用域。
			- Function scope: 在函数中的变量的作用域。
		- 此外，使用 `let` 和  `const` 声明的变量，比使用 `var` 声明的变量多一个额外的作用域 (原因见下文 Variable hoisting)，即：
			- Block scope: 在代码块中的变量的作用域。
			- ``` js
			  // 如下代码报错，因为 y 的作用域只在 if 代码块中
			  if (Math.random() > 0.5) {
			  	const y = 5;
			  }
			  console.log(y); // ReferenceError: y is not defined
			  
			  // 如下代码正常运行，因为 var 关键字导致 x 作用域提升
			  if (true) {
			  	var x = 5;
			  }
			  console.log(x); // x is 5
			  ```
		- 在所有函数之外声明的变量，被称为 *global* variable .
		- 在函数内声明的变量，被称为 *local* variable .
	- ### Variable hoisting
		- ``` js
		  // 变量被提升至全局作用域的顶部
		  console.log(x === undefined); // true
		  var x = 3;
		  
		  (function () {
		    // 变量被提升至函数顶部
		    console.log(x); // undefined
		    var x = "local value";
		  })();
		  ```
		- 使用 var 声明变量，会导致变量的 *declaration* 被提升至函数的顶部，或全局作用域的顶部。
		  id:: 66c8624d-b9bd-4de0-9360-0dd420056b9a
		- 但是，只是 *declaration* 提升了, *initialization* 并没有被提升，所以如果在变量的声明语句前使用这个变量，将会是赋值前的默认值 `undefined` 。
		- 上述代码与如下代码等价:
			- ``` js
			  var x;
			  console.log(x === undefined); // true
			  x = 3;
			  
			  (function () {
			    var x;
			    console.log(x); // undefined
			    x = "local value";
			  })();
			  ```
	- ### var and let
		- `var` 允许如下的代码正常执行 (而如下代码的写法会带来混乱)：
			- ``` js
			  // case1
			  name = "tom"
			  var name = "jack"
			  
			  // case2
			  var name = "tom"
			  var name = "jack"
			  ```
		- 若上述代码使用 `let` , 将会抛出异常。
		- 所以我们应弃用 `var` 而改用 `let` ，避免造成混乱。
	- ### 变量类型
		- #### 五种类型
			- Numbers
			- Strings
			- Booleans
			- Arrays
			- Objects
		- #### Strings
			- 可以使用 `""` 和 `''`  声明一个普通字符串。
			- 可以使用 ` 声明 *template literals (模板字符串)* , 可以嵌入 **变量和表达式**
				- ``` js
				  const name = "Mahalia";
				  const greeting = `Hello ${name}`;
				  ```
		- #### Arrays
			- 声明数组
			- ``` js
			  let myNameArray = ["Chris", "Bob", "Jim"];
			  ```
		- #### Objects
			- ``` js
			  // 声明对象
			  let dog = { name: "Spot", breed: "Dalmatian" };
			  
			  // 使用对象的属性
			  dog.name;
			  ```
	- ### Dynamic typing
		- JS 是 *动态类型语言 (dynamically typed language)* :
			- 变量声明时，不可以也无需指定数据类型;
			- 变量初始化后，可以被赋值为其他类型的数据.
		- ### const
			- `const` 声明常量。
				- 声明时必须赋值。
				- 赋值后不可再赋值。
			- ``` js
			  const age = 10;
			  ```
		- ### typeof
			- 使用 typeof 可以查看 **变量或常量** 的类型。
			- ``` js
			  const age = 10;
			  // 输出 number
			  console.log(typeof age);
			  
			  let name = "Jack" ;
			  // 输出 string
			  console.log(typeof name);
			  ```
- ## Loop
	- ### for...of
		- ``` js
		  const resetParas = document.querySelectorAll(".resultParas p");
		  for (const resetPara of resetParas) {
		    resetPara.textContent = "";
		  }
		  ```
- ## Function
	- ### 基本语法
		- ``` js
		  // 声明函数
		  function hello(name) {
		    console.log("Hello World! " + name);
		  }
		  
		  // 调用函数
		  hello("Vincent");
		  ```
	- ### Arrow Function
		- ``` js
		  // 声明函数
		  const hello = (name) => {
		    return "Hello World! " + name);
		  }
		  
		  // 当只有一个参数时的简略写法
		  const hello = name => "Hello World! " + name;
		  
		  // 调用函数
		  hello("Vincent");
		  ```
	- ### Method in Object
		- ``` js
		  // 定义对象
		  const people = {
		    age: 20,
		    name: "Vincent",
		    // 声明对象的方法
		    hello() {
		      return "Hello, " + this.name;
		    }
		  };
		  
		  // 执行方法
		  people.hello();
		  ```
- ## Destructuring 解构
	- ### Object 的解构
		- ``` js
		  // 定义对象
		  const people = {
		    age: 20,
		    name: "Vincent",
		    // 声明对象的方法
		    hello() {
		      return "Hello, " + this.name;
		    }
		  };
		  
		  // 将对象的属性赋值给同名变量
		  const {age, name, hello} = people;
		  
		  // 将对象的属性赋值给不同名的变量
		  const {age: newAge, name: newName, hello: newHello} = people;
		  ```
	- ### Array 的解构
		- ``` js
		  const langs = ["en", "zh", "jp"]; 
		  // 将数组元素赋给变量
		  const [l0, l1, l2] = langs;
		  ```
		-
- ---
- ## 参考
	- [MDN JavaScript Guide - Grammar and types](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Grammar_and_types)
	  logseq.order-list-type:: number
	- logseq.order-list-type:: number