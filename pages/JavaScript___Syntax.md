## Comment
	- ``` js
	  // single line comment
	  
	  /*
	    multi-line
	    comment
	  */
	  ```
- ## Variable
	- ### var vs let
		- `var` 允许如下的代码正常执行 (而如下代码的写法会带来混乱)：
			- ``` js
			  // case1
			  name = "tom"
			  var name = "jack"
			  
			  // case2
			  var name = "tom"
			  var name = "jack"
			  ```
		- 所以新版本的 JS 弃用 `var` ，而 改用 `let` 作为声明变量的关键。
		- 若上述代码使用 `let` , 将会抛出异常。
	- ### 变量命名规范
		- 只使用如下字符:
		  logseq.order-list-type:: number
			- Latin characters: `0-9` 、 `a-z` 、 `A-Z`
			  logseq.order-list-type:: number
			- Underscore character: `_`
			  logseq.order-list-type:: number
		- `0-9` 和 `_` 不要放在开头
		  logseq.order-list-type:: number
		- 使用 `lower camel case`
		  logseq.order-list-type:: number
		- 变量名要做到顾名思义
		  logseq.order-list-type:: number
		- ==注意: JS 变量名称大小写敏感。==
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
			  // 声明象
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
- ## loop
	- ### for...of
		- ``` js
		  const resetParas = document.querySelectorAll(".resultParas p");
		  for (const resetPara of resetParas) {
		    resetPara.textContent = "";
		  }
		  ```
		-