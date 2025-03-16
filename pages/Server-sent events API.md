tags:: [[Server-sent events]]
---

- ## EventSource 原理
	- 创建一个 `EventSource` 实例, 会打开到 HTTP 服务器的持久连接 .
	  logseq.order-list-type:: number
	- 连接保持期间, 服务器以 `text/event-stream` 格式发送消息 (message) , 消息以事件 (event) 的形式传递给客户端代码 .
	  logseq.order-list-type:: number
		- 如果消息中存在 `event` 字段，则触发与 `event` 字段值同名的事件 ;
		- 如果消息中不存在 `event` 字段，则触发一个通用的 `message` 事件 .
			- 可以事先通过 `EventSource.onmessage` 属性设置 Event Handler .
	- 调用 `EventSource.close()` 关闭连接 .
	  logseq.order-list-type:: number
- ## 连接数限制
	- 当不使用 `HTTP/2` 时:
		- 每个浏览器所有 Tab 中, 同一域名, 只能打开最多 6 个 SSE 连接.
	- 当使用 `HTTP/2` 时:
		- 服务器和客户端之间, 会协商最大连接数, 默认为 100 .
- ## 参考
	- [MDN - Web API - EventSource](https://developer.mozilla.org/en-US/docs/Web/API/EventSource)
	  logseq.order-list-type:: number
	- [MDN - Using server-sent events](https://developer.mozilla.org/en-US/docs/Web/API/Server-sent_events/Using_server-sent_events)
	  logseq.order-list-type:: number