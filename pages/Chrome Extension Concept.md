tags:: [[Chrome Extension]]
---

- ## Extension files
	- ### 文件结构
		- 图片来源: `https://wd.imgix.net/image/BhuKGJaIeLNPW9ehns59NfwqKxF2/Txq5CxeXjQz7i4wmP8zO.png?auto=format&w=439`
		- ![image.png](../assets/image_1699013507049_0.png){:height 644, :width 434}
	- ### 常用文件
		- manifest
		- service worker
		- content scripts
		- popup and other pages
	- ### manifest
		- extension 唯一的必要文件 .
		- 文件名必须为 `manifest.json` , 且必须位于 extension 的根目录 .
		- 记录一些重要的 `metadata` .
	- ### service worker
		- 监听 和 处理 `browser events` (如 关闭一个 tab) .
		- 可以调用所有 `Chrome Api` .
		- 不能直接与网页内容交互 .
	- ### content scripts
		- 可以在网页中执行 Javascript .
		- 可以读取和修改网页的 `DOM`.
		- 可以直接调用部分 `Chrome Api`.
		- 可以通过与 `service worker` 交互, 间接调用剩下的那部分 `Chrome Api` .
	- ### popup and other pages
		- Extension 可以包含各种 HTML 页面:
			- 一个 [popup](https://developer.chrome.com/docs/extensions/mv3/user_interface/#popup)
			  logseq.order-list-type:: number
			- 一个 [options page](https://developer.chrome.com/docs/extensions/mv3/options/)
			  logseq.order-list-type:: number
			- [其它 HTML pages](https://developer.chrome.com/docs/extensions/mv3/architecture-overview/#html-files)
			  logseq.order-list-type:: number
- ## manifest
	- 只有三个字段是必须的:
		- `"manifest_version"`
		- `"name"`
		- `"version"`
	-
	-
- ---
- ## 参考
	- [Get Started Guide](https://developer.chrome.com/docs/extensions/mv3/getstarted/)
	  logseq.order-list-type:: number
	- [Architecture overview](https://developer.chrome.com/docs/extensions/mv3/architecture-overview/)
	  logseq.order-list-type:: number
	- logseq.order-list-type:: number