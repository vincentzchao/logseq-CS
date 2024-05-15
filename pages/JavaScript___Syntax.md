## Comment
	- ``` js
	  // single line comment
	  
	  /*
	    multi-line
	    comment
	  */
	  ```
- ## string
	- 可以使用 `""` 和 `''`  声明一个普通字符串。
	- 可以使用 ` 声明 *template literals (模板字符串)* , 可以嵌入 **变量和表达式**
		- ``` js
		  const name = "Mahalia";
		  const greeting = `Hello ${name}`;
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