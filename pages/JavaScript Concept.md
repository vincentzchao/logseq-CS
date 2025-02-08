tags:: [[JavaScript]]
---

- ## 什么是 JavaScript
	- 参见: [What is JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Introduction#what_is_javascript)
	- JavaScript 是一种 跨平台的面向对象脚本语言 (cross-platform, object-oriented scripting language) .
- ## JavaScript 的组成及其规范
	- 参见: [What is JavaScript](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Introduction#what_is_javascript)
	- 我们常说的 JavaScript 可能是如下几种：
		- `Core JavaScript`
		  logseq.order-list-type:: number
		- `Client-side JavaScript`
		  logseq.order-list-type:: number
		- `Server-side JavaScript`
		  logseq.order-list-type:: number
	- ### Core JavaScript
		- 即 JavaScript 语言核心。
		- 包含一组标准对象 (如 `Array` ， `Map` ，和 `Math` ) , 以及一组核心语言元素 (如 运算符、控制结构和语句) 。
		- `Core JavaScript` 的规范由 `ECMAScript` 定义  (具体参见 [[ECMAScript Concept]] ) .
	- ### Client-side JavaScript
		- 相当于 `Core JavaScript` + `Web APIs` + `浏览器自定义 API`
		- `Web APIs`：
			- `Document Object Model (DOM)` : 操作页面元素。 
			  logseq.order-list-type:: number
				- DOM 规范: [whatwg - DOM Spec](https://dom.spec.whatwg.org/)
			- `Browser Object Model (BOM)` : 操作浏览器。 
			  logseq.order-list-type:: number
				- BOM 并没有一个明确的规范
				- logseq.order-list-type:: number
			- 其他 Web APIs。
			  logseq.order-list-type:: number
				- 有些有规范；
				- 有些没有规范，由浏览器自己定义、自己实现。
	- ### Server-side JavaScript
		- 补充 `与 running JavaScript on a server 相关` 的对象。
	- ### JavaScript 与 ECMAScript
		-
	- ### JavaScript 没有标准实现
		-
-
	-
	-
- ## Interpreted VS compiled
	- JavaScript 采用 **just-in-time compiling (即时编译)** 技术，在代码被使用时，会被编译成 binary 格式执行，以提高性能。
	- 但是，由于编译是在 **run time** 发生的 (而不是事先执行) ，所以 JavaScript 仍然被认为是 `Interpreted Language` 。
- ---
- ## 参考
	- [MDN - What is JavaScript?](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/First_steps/What_is_JavaScript)
	  logseq.order-list-type:: number
	- [MDN - JavaScript Introduction](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Introduction)
	  logseq.order-list-type:: number
	- logseq.order-list-type:: number