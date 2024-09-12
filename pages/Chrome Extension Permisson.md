tags:: [[Chrome Extension]]
---

- ## activeTab permission
	- 当用户 `invoke` 这个这个扩展 (比如点击 icon) , 用户便有 **权限** 暂时访问当前的 `tab` .
	- ~~当用户在当前这个 `tab` , 这个 **权限** 一直持续, 直到用户离开或者关闭当前 `tab` .~~
	- 从 `M72` 开始, 权限将在当前 `origin` (由 **协议//:域名:端口** 唯一确定) 一直持续, 直到换了 `origin` .
	-
	-
- ---
- ## 参考
	- [The activeTab permission](https://developer.chrome.com/docs/extensions/mv3/manifest/activeTab/)
	  logseq.order-list-type:: number
	- logseq.order-list-type:: number