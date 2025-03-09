tags:: [[HTML]]
---

- ## Boolean attributes
	- 参见: [MDN - Boolean attribute](https://developer.mozilla.org/en-US/docs/Glossary/Boolean/HTML)
	- 表示 true 或 false 值的属性。
		- 表示 true 的情况：
		  logseq.order-list-type:: number
			- 只有属性名，没有等号和属性值: `checked`
			  logseq.order-list-type:: number
			- 属性名和等号都有，但是属性值为空字符串: `checked=""`
			  logseq.order-list-type:: number
			- 属性名和等号都有，属性值等于属性名，大小写不敏感: `checked="checked"`
			  logseq.order-list-type:: number
			- 属性名和等号都有，属性值为除了上述情况之外的任意字符串: `checked="嘻嘻嘻"` ( ==此方式不推荐== )
			  logseq.order-list-type:: number
				- ==注意：虽然现代浏览器把除了空字符串外的所有值，都认为是 true ，但我们不应该依赖这个行为。==
		- 表示  false 的情况：
		  logseq.order-list-type:: number
			- 不填这个属性。
	- ``` html
	  <!-- The following checkboxes will be checked on initial rendering -->
	  <input type="checkbox" checked />
	  <input type="checkbox" checked="" />
	  <input type="checkbox" checked="checked" />
	  <input type="checkbox" checked="Checked" />
	  <input type="checkbox" checked="嘻嘻嘻" />
	  
	  <!-- The following checkbox will not be checked on initial rendering -->
	  <input type="checkbox" />
	  ```
- ## Global Attribute
	-