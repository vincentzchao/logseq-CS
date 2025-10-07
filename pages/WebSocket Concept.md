tags:: [[WebSocket]]
---

- ## 什么是 WebSocket
	- WebSocket 是一项可以让 **浏览器 和 服务器 之间建立一个双向的交互式通信会话** 的技术.
- ## WebSocket Event
	- 参见: [[WebSocket Event]]
- ## WebSocket Handshake
	- ### Client handshake request
		- #### 格式
			- 客户端要与服务端建立连接时, 先会发送一个握手请求.
			- 客户端发起的握手请求, 是一个标准的 HTTP 请求, 格式如下:
				- ``` http
				  GET /chat HTTP/1.1
				  Host: example.com:8000
				  Upgrade: websocket
				  Connection: Upgrade
				  Sec-WebSocket-Key: dGhlIHNhbXBsZSBub25jZQ==
				  Sec-WebSocket-Version: 13
				  ```
				- ==注意==
					- 必须是 `GET` 请求.
					  logseq.order-list-type:: number
					- `HTTP` 版本必须大于等于 `1.1` .
					  logseq.order-list-type:: number
					- 除了上述请求头外, 可能还会有 `User-Agent` , `Referer` , `Cookie` 等常见请求头.
					  logseq.order-list-type:: number
		- #### 服务器错误处理
			- 如果服务器无法理解任何请求头或其值不正确, 应返回 `400 Bad Request` , 并立即关闭连接.
			  logseq.order-list-type:: number
				- 按照惯例, HTTP 响应正文中, 应该说明握手失败的原因.
			- 如果服务器不支持请求的 WebSocket 版本, 应返回 `Sec-WebSocket-Version` 响应头, 值为服务器支持的版本.
			  logseq.order-list-type:: number
	- ### Server handshake response
		- 针对 Client handshake request 服务器会给一个响应, 格式如下:
			- ``` http
			  HTTP/1.1 101 Switching Protocols
			  Upgrade: websocket
			  Connection: Upgrade
			  Sec-WebSocket-Accept: s3pPLMBiTxaQ9kYGzzhZRbK+xOo=
			  ```
			- `{Sec-WebSocket-Accept}` =  `Base64( SHA-1( {Sec-WebSocket-Key} + "258EAFA5-E914-47DA-95CA-C5AB0DC85B11" ) )`
				- 之所以需要这个响应头, 是为了让客户端可以判断服务端是否支持 WebSocket .
				- 如果服务器不支持 WebSocket , 可能会将客户端后续发送的数据解析为 HTTP 请求, 这可能会导致安全问题.
			- ==注意==
				- 每行以 `\r\n` 结尾, 最后一行需要额外加一个 `\r\n` .
				  logseq.order-list-type:: number
		- 服务器一旦发送握手响应, 就代表握手成功, 双方都可以发送数据了.
-
	-
- ## 参考
	- [Writing WebSocket servers](https://developer.mozilla.org/en-US/docs/Web/API/WebSockets_API/Writing_WebSocket_servers)
	  logseq.order-list-type:: number