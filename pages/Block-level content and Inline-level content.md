tags:: [[HTML]], [[CSS]]
---

- ## Block-level element and Inline element
	- 历史上，HTML 元素曾被分为 "block-level" elements 和 "inline" elements 。
	- 但如今，HTML 元素不这么划分， "block-level" 还是 "inline" ，作为一种表现特征，现在由 CSS 来指定。
	- 通过修改 CSS ，可以决定网页内容是 Block-level content 还是 Inline-level content 。
		- 但，元素都有默认 CSS 样式，所以，默认的 CSS 样式可以决定，这个元素，默认是 Block-level  还是 Inline-level 。
		- 默认是 `Block-level content` 的元素 (或保留旧称 `Block-level element` ) 有：
			- `<p></p>` , `<div></div>` 等
		- 默认是 `Inline-level content` 的元素 (或保留旧称 `Inline element` ) 有：
			- `<a></a>` , `<em></em>` , `<strong></strong>` , `<span></span>` 等
- ## Block-level content
	- 参与 `block layout` (块布局) 的内容，就被称为 `block-level content` 。
	- 在  `block layout` 中：
		- 盒子从上到下垂直排列。
		  logseq.order-list-type:: number
		- 每个盒子的左边缘，接触它的父容器的左边缘。
		  logseq.order-list-type:: number
		- 块级内容始终从新的一行开始。
		  logseq.order-list-type:: number
			- 如，在 `horizontal writing modes` 中 (如英文) ，它占据其父容器的整个水平空间，以及与其内容等高的垂直空间。
				- 修改 ` writing-mode ` 可以修改这一行为。
	- **块级内容** 在页面上形成可见的块。
	- **块级内容** 会在它之前的任何内容之后另起一行显示，而它之后的任何内容也会另起一行显示。
	- **块级内容** 通常是结构化的元素，如 headings, paragraphs, lists, navigation menus, or footers 。
	- **块级内容** 可以被嵌套在块级内容中，而不可以被嵌套在行级内容中。
- ## Inline elements
	- **行内元素** 被包含在 **块级元素** 中，并且它通常仅包含网页的一小部分（即不包含整个段落或大量内容）。
	- **行内元素** 之前的内容如果也是 **行内元素** ，则它不会另起一行显示。
	-
- ## 参考
	- [MDN - Block-level content](https://developer.mozilla.org/en-US/docs/Glossary/Block-level_content)
	  logseq.order-list-type:: number
	- [MDN - Inline-level content](https://developer.mozilla.org/en-US/docs/Glossary/Inline-level_content)
	  logseq.order-list-type:: number
	-
	- logseq.order-list-type:: number