tags:: [[Whitespace Character]]
---

- ## 如何处理 HTML 中的 Whitespace
	- 文本内容之间的 Whitespace 会被解析为单个空白字符。
	  logseq.order-list-type:: number
	- 块级元素：
	  logseq.order-list-type:: number
		- 外部的 Whitespace 会被忽略。
		  logseq.order-list-type:: number
		- 元素内开始标签到文本内容之间的 Whitespace ，和文本内容到结束标签之间的 Whitespace，会被忽略。
		  logseq.order-list-type:: number
	- 行内元素：
	  logseq.order-list-type:: number
		- 行内元素之间的 Whitespace 会被解析为单个空白字符。
		  logseq.order-list-type:: number
		- 元素内开始标签到文本内容之间的 Whitespace ，和文本内容到结束标签之间的 Whitespace，会被忽略。
		  logseq.order-list-type:: number
	- ``` html
	  <!doctype html>
	  
	    <h1>      Hello      World!     </h1> 
	    <a>link</a>  <span> span-text1</span><span> span-tex2</span> 
	  ```
-