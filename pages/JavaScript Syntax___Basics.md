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
		- 变量在使用前必须声明 (虽然在声明一个变量前，对其进行赋值不会报错，但是可能会出问题)。
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
	- ### const
		- `const` 声明常量。
			- 声明时必须赋值。
			- 赋值后不可再赋值。
		- ``` js
		  const age = 10;
		  ```
	- ### Global Variables
		- 全局变量实际上就是 *global object* (全局对象) 的属性。
		- 如果在 webpage 中，这个对象就是 `window` .
			- 可以使用 `window.${变量名}` 、 `windows.globalThis.${变量名}` 或 `globalThis.${变量名}` 进行访问。
- ## Data Types
	- ### Eight Data Types
		- Seven Primitives
		  logseq.order-list-type:: number
			- Boolean
			  logseq.order-list-type:: number
				- `true` or `false`
			- `null`
			  logseq.order-list-type:: number
			- `undefined`
			  logseq.order-list-type:: number
			- Number
			  logseq.order-list-type:: number
				- integer
				- floating point number
			- BigInt
			  logseq.order-list-type:: number
				- 具有任意精度 (arbitrary precision) 的 integer
			- String
			  logseq.order-list-type:: number
			- Symbol
			  logseq.order-list-type:: number
		- Object
		  logseq.order-list-type:: number
			- array 也属于 object
			- function 也属于 object
	- ### Dynamic typing
		- JS 是 *动态类型语言 (dynamically typed language)* :
			- 变量声明时，不可以也无需指定数据类型;
			- 变量初始化后，可以被赋值为其他类型的数据.
	- ### typeof
		- 使用 `typeof` 可以查看 **变量或常量** 的类型。
		- ``` js
		  const age = 10;
		  // 输出 number
		  console.log(typeof age);
		  
		  let name = "Jack";
		  // 输出 string
		  console.log(typeof name);
		  ```
- ## String Literals
	- ### Single Quotes or Double Quotes
		- 可以使用 `""` 和 `''`  声明一个普通字符串。
	- ### Template Literals
		- 可以使用 ` 声明 *template literals (模板字符串)* , 可以嵌入 **变量和表达式**
			- ``` js
			  const name = "Mahalia";
			  const greeting = `Hello ${name}`;
			  ```
	- ### Converting strings to numbers
		- 使用 `parseInt()` 和 `parseFloat()` .
		  logseq.order-list-type:: number
			- ``` js
			  // 第二个参数是 radix ，表示是几进制
			  parseInt("101", 2); // 5
			  ```
		- 使用 `+` 操作符
		  logseq.order-list-type:: number
			- ``` js
			  (+"1.1") + (+"1.1"); // 2.2
			  
			  // 上面代码的括号可以去掉
			  +"1.1" + +"1.1"; // 2.2
			  ```
- ## Array Literals
	- ### Array Literals
		- ``` js
		  // ["Chris", "Bob", "Jim"] 部分被称为 Array Literal
		  let myNameArray = ["Chris", "Bob", "Jim"];
		  ```
	- ### Extra Commas
		- ``` js
		  const fish = ["Lion", , "Angel", ,];
		  console.log(fish); // ['Lion', empty, 'Angel', empty] 
		  console.log(fish.length); // 4
		  console.log(fish[0]); // Lion
		  console.log(fish[2]); // Angel
		  console.log(fish[1]); // undefined
		  ```
		- 末尾的额外逗号，不会引起语法错误。
		  logseq.order-list-type:: number
		- 非末尾的额外逗号，会导致产生一个 `空槽 (empty slot)` .
		  logseq.order-list-type:: number
			- 虽然使用索引访问空槽处的元素，值为 `undefined` ，但其本质与 `undefined` 不同。
				- 因为，在使用一些遍历数组的方法 (array-traversing methods) 时，空槽处的元素会被跳过。
				- 而如果值为 `undefined` 则不会。
			- 如果一定要声明 `empty slot` ，最好加上注释：
				- ``` js
				  const myList = ["home", /* empty */, "school", /* empty */, ];
				  ```
- ## Number Literals
	- ### Integer Literals
		- octal 八进制
			- `0` 或 `0o` 或 `0O` 开头的数字
		- hexadecimal 十六进制
			- `0x` 或 `0X` 开头的数字
		- binary 二进制
			- `0b` 或 `0B` 开头的数字
	- ### BigInt Literals
		- 在 Integer Literals 的末尾加上字母 `n` 即可。
		- 但是，八进制中，类似 `0123n` 以 `0` 开头的 BigInt Literals 是非法的。
	- ### Floating-point literals
		- 语法: `[digits].[digits][(E|e)[(+|-)]digits]`
		- 注意，浮点数字面量只支持十进制。
		- ``` js
		  3.1415926
		  .123456789
		  // 相当于 3.1 * (10 ^ 12)
		  3.1E+12
		  .1e-23
		  ```
- ## Object Literals
	- ### Valid Identifier Property
		- ``` js
		  let dog = { name: "Spot", breed: "Dalmatian" };
		  
		  console.log(dog.name);
		  console.log(dog["name"]);
		  ```
		- 如果属性名称是合法的标识符：
			- 则可以使用 `object.property` 或 `object.["property"]` 或 `object.['property']` 三种方式访问属性。
	- ### Numeric property name
		- 如果使用数字 (包括小数) 作为属性名称：
			- 则可以使用 `object.[property]` 或 `object.["property"]` 或 `object.['property']` 三种方式访问属性。
		- ``` js
		  const car = { 1.3: "Jeep", 7: "Mazda" };
		  
		  console.log(car[1.3]); // Jeep
		  console.log(car[7]); // Mazda
		  ```
	- ### Invalid Identifier Property
		- 如果使用 除数字以外 的非法标识符作为属性名称，则：
			- 在声明时，必须加上引号 (单引号和双引号都行) 。
			- 在访问时，则只能使用 `object.["property"]` 或 `object.['property']` 两种方式。
		- ``` js
		  const unusualPropertyNames = {
		    '': 'An empty string',
		    '!': 'Bang!'
		  }
		  
		  console.log(unusualPropertyNames[""]); // An empty string
		  console.log(unusualPropertyNames["!"]); // Bang!
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