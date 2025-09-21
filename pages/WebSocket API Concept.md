tags:: [[WebSocket API]]
---

- ## WebSocket, WebSocketStream 与 WebTransport
	- Web API 提供了 `WebSocket` 和 `WebSocketStream` 两个接口, 用于创建和使用 WebSocket 连接
	- [[WebSocket Interface]]
		- 稳定且被广泛支持.
		- 但是, 不支持背压 (backpressure).
			- 即, 当消息到达的速度, 超过程序处理速度时:
				- 要么会由于缓存消息, 导致内存被填满;
				- 要么会由于消息处理太频繁, 导致 CPU 使用率到达 100%, 最终导致无响应 (unresponsive).
				- 要么以上二者都有.
	- [[WebSocketStream Interface]]
		- 基于 Promise 实现, 使用 [[Streams API]] 来处理消息的 接收和发送, 所以可以处理背压.
		- 但是 `WebSocketStream` 并非标准 API , 支持的浏览器比较少.
	- [[WebTransport API]]
		- WebTransport 是一个低级 API (low-level), 它能提供 `Websocket` 和 `WebsocketStream` 不支持的功能, 比如:
			- unidirectional streams
			- out-of-order delivery
			- unreliable data transmission via datagrams
		- 缺点:
			- 使用复杂.
			  logseq.order-list-type:: number
			- 支持的浏览器不多.
			  logseq.order-list-type:: number
- ## WebSocket Event
	- `close` event : `WebSocket` 连接关闭时触发.
	- `error` event : 由于错误 (如数据无法发送) 导致 `WebSocket` 连接关闭时  (此时也会触发 `close` 事件) 触发.
	- `message` event : 接收数据时触发.
	- `open` event : `WebSocket` 连接打开时触发.
	- 可以使用 `addEventListener()` 或 `on{eventname}` property 设置 event handler .
		- ``` js
		  // Create WebSocket connection.
		  const socket = new WebSocket("ws://localhost:8080");
		  
		  // Connection opened
		  socket.addEventListener("open", (event) => {
		    socket.send("Hello Server!");
		  });
		  
		  // Listen for messages
		  socket.addEventListener("message", (event) => {
		    console.log("Message from server ", event.data);
		  });
		  ```
- ## 参考
	- [MDN - The WebSocket API (WebSockets)](https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API)
	  logseq.order-list-type:: number
	- [MDN - Web API - WebSocket](https://developer.mozilla.org/en-US/docs/Web/API/WebSocket)
	  logseq.order-list-type:: number