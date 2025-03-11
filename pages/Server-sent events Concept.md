tags:: [[Server-sent events]]
---

- ## 作用
	- 用于服务端传送流式数据到客户端.
- ## 规范
	- 相关规范: [HTML Spec - 9.2 Server-sent events](https://html.spec.whatwg.org/multipage/server-sent-events.html)
- ## MIME type
	- MIME type 需要使用 `text/event-stream`
	- 但是这个 [IANA Media Types 汇总](https://www.iana.org/assignments/media-types/media-types.xhtml) 中并没有找到, `text/event-stream` .
		- 貌似, IANA 暂时没有接受这个 MIME Type 的注册;
		- 但各大浏览器基本已支持此类型, 所以它已成为事实标准.
	-
-
- ## 参考
	- [MDN - Server-sent events](https://developer.mozilla.org/en-US/docs/Web/API/Server-sent_events)
	  logseq.order-list-type:: number