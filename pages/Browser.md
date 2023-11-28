tags:: [[Front-End]]
---

-
- ## 渲染的顺序
	- 参考: [How the web works](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/How_the_Web_works#order_in_which_component_files_are_parsed)
	- 1. 获取 `html` 文件，并解析其中的 `<link>` 和 `<script>` 标签。
	  2. 发出请求获取 `css` 和 `javascript` 文件，解析  `css` 和 `javascript` 文件。
	  3. 在内存中生成 `DOM` 和 `CSSOM` ，然后编译并执行 `JavaScript` 。
	  4. 根据上一步的三个元素，渲染画面。
-