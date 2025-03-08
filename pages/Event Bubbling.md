alias:: [[事件冒泡]]
tags:: [[Web Event]], [[JavaScript]] 
---

- ## Event Bubbling
	- ### 什么是 Event Bubbling
		- ``` js
		  <body>
		    <div id="container">
		      <button>Click me!</button>
		    </div>
		    <pre id="output"></pre>
		  </body>
		  
		  const output = document.querySelector("#output");
		  function handleClick(e) {
		    output.textContent += `You clicked on a ${e.currentTarget.tagName} element\n`;
		  }
		  
		  const container = document.querySelector("#container");
		  const button = document.querySelector("button");
		  
		  document.body.addEventListener("click", handleClick);
		  container.addEventListener("click", handleClick);
		  button.addEventListener("click", handleClick);
		  ```
		- 如上代码, `<button>` 的点击事件, 会向上传播到 `<div>` , 再向上传播到 `<body>` , 这被描述为 **bubbles up** 。
		- 点击按钮，会在页面呈现：
			- ``` js
			  You clicked on a DIV element
			  You clicked on a BUTTON element
			  You clicked on a BODY element
			  ```
	- ### stopPropagation() 阻止事件冒泡
		- ``` js
		  <button>Display video</button>
		  
		  <div class="hidden">
		    <video>
		      <source
		        src="https://interactive-examples.mdn.mozilla.net/media/cc0-videos/flower.webm"
		        type="video/webm" />
		      <p>
		        Your browser doesn't support HTML video. Here is a
		        <a href="rabbit320.mp4">link to the video</a> instead.
		      </p>
		    </video>
		  </div>
		  
		  const btn = document.querySelector("button");
		  const box = document.querySelector("div");
		  const video = document.querySelector("video");
		  
		  btn.addEventListener("click", () => box.classList.remove("hidden"));
		  
		  video.addEventListener("click", (event) => {
		    event.stopPropagation();
		    video.play();
		  });
		  
		  box.addEventListener("click", () => box.classList.add("hidden"));
		  ```
		- 如上代码, 通过调用 `stopPropagation()` 可以防止事件向上传播.
			- 这样, 发生在子元素的事件, 仅会触发子元素的 `event handler` , 不会触发父元素的 `event handler`
- ## Event Capture
	- ### 什么是 Event Capture
		- 与 **Event Bubbling** 相反, **Event Capture** 的事件, 是从最外层的元素, 传播到最里层的元素.
		- **Event Capture** 默认是禁用的, 需要在调用 `addEventListener()` 方法时, 设置 `options.capture` 为 `true` .
		- ``` html
		  <!DOCTYPE html>
		  <html lang="en">
		  
		  <head>
		    <meta charset="UTF-8">
		    <meta name="viewport" content="width=device-width, initial-scale=1.0">
		    <title>Document</title>
		  </head>
		  
		  <body>
		    <div id="container">
		      <button>Click me!</button>
		    </div>
		    <pre id="output"></pre>
		  
		    <script>
		      const output = document.querySelector("#output");
		  
		      function handleClick(e) {
		        output.textContent += `You clicked on a ${e.currentTarget.tagName} element\n`;
		      }
		  
		      const container = document.querySelector("#container");
		      const button = document.querySelector("button");
		  
		      document.body.addEventListener("click", handleClick);
		      container.addEventListener("click", handleClick, {
		        capture: true
		      });
		      button.addEventListener("click", handleClick);
		    </script>
		  </body>
		  
		  </html>
		  ```
		- 点击按钮, 会在页面呈现：
			- ``` js
			  You clicked on a DIV element
			  You clicked on a BUTTON element
			  You clicked on a BODY element
			  ```
	- ### Event Handler 的执行顺序
		- 事件触发时, `Event Handler` 的执行逻辑是这样的：
			- 从外层元素往内层元素遍历, 判断 `options.capture` 是否为 `true` .
			  logseq.order-list-type:: number
				- 是, 则此元素的 **Event Handler** 触发。
				- 否, 则此元素的 **Event Handler** 暂时不触发。
			- 然后从内层元素往外层元素遍历, 依次执行 `Event Handler` (即按 **Event Bubbling** 的顺序执行), 执行过的就不用执行了.
			  logseq.order-list-type:: number
	- ### 为什么 Event Bubbling 与 Event Capture 同时存在
		- 因为在史前时代, Netscape 只使用事件捕获, 而 Internet Explorer 只使用事件冒泡.
		- 后来, W3C 在指定标准时, 决定两者共存。
- ## Event delegation
	- 有时候, 我们需要给大量子元素都添加 **Event Handler** , 这会比较繁琐;
	- 此时, 我们可以利用 **Event Bubbling** 的性质, 将事件委托给父元素进行处理 (即 Event delegation).
	- ``` html
	  <!DOCTYPE html>
	  <html lang="en">
	  
	  <head>
	    <meta charset="UTF-8">
	    <meta name="viewport" content="width=device-width, initial-scale=1.0">
	    <title>Document</title>
	    <style>
	      #container {
	        display: grid;
	        grid-template-columns: repeat(4, 1fr);
	        grid-auto-rows: 100px;
	      }
	    </style>
	  </head>
	  
	  <body>
	    <div id="container">
	      <div class="tile"></div>
	      <div class="tile"></div>
	      <div class="tile"></div>
	      <div class="tile"></div>
	      <div class="tile"></div>
	      <div class="tile"></div>
	      <div class="tile"></div>
	      <div class="tile"></div>
	      <div class="tile"></div>
	      <div class="tile"></div>
	      <div class="tile"></div>
	      <div class="tile"></div>
	      <div class="tile"></div>
	      <div class="tile"></div>
	      <div class="tile"></div>
	      <div class="tile"></div>
	    </div>
	  
	    <script>
	      function random(number) {
	        return Math.floor(Math.random() * number);
	      }
	  
	      function bgChange() {
	        const rndCol = `rgb(${random(255)} ${random(255)} ${random(255)})`;
	        return rndCol;
	      }
	  
	      const container = document.querySelector("#container");
	  
	      container.addEventListener("click", (event) => {
	        event.target.style.backgroundColor = bgChange();
	      });
	    </script>
	  </body>
	  
	  </html>
	  ```
- ## target 与 currentTarget
	- **Event Interface** 的 `target` 表示触发事件的元素.
	- **Event Interface** 的 `currentTarget` 表示 **Event Handler** 所关联的元素.
	- 在 Bubble up 的过程中 `target` 保持不变, 而  `currentTarget` 会一直变化.
- ## Phases
	-
- ## Reference
	- [DOM Event 可视化工具](https://domevents.dev/)
	-
- ---
- ## 参考
	- [MDN - Event Bubbling](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Scripting/Event_bubbling)
	  logseq.order-list-type:: number
	- [JavaScript 和 React 中的事件冒泡和事件捕获——初学者指南](https://www.freecodecamp.org/chinese/news/event-propagation-event-bubbling-event-catching-beginners-guide-2/)
	  logseq.order-list-type:: number
	- logseq.order-list-type:: number