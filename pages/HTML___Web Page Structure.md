tags:: [[HTML]]
---

- ## 网页的基本结构
	- ### 基本结构
		- #### header
			- 顶部的大长条，包含 **大标题** 、 **Logo** ，可能还有 **标语** 。
			- 跳转页面时 **保持不变** 。
		- #### navigation bar
			- 可链接到网站的 **主要页面** 。
			- 通常呈现为 **菜单按钮** **链接** **标签页** 等。
			- 跳转页面时 **保持不变** 。
		- #### main content
			- 网页中间大片区域，包含当前网页大部分的 **唯一内容** (每个网页都不一样，比如：视频 文章 地图 等) 。
		- #### sidebar
			- 包含一些 **次要** 的 **信息** **链接** **引用** **广告** 等，通常与 **main content** 内容相关 (例如，在新闻文章页面上，侧边栏可能包含作者的个人简介，或相关文章的链接) 。
			- 在某些情况下，这里也可能是一个 **二级导航** , 如 文章的目录。
		- #### footer
			- 页面底部的一个长条。
			- 通常包含 **细则** **版权声明** **联系方式** 等 **通用信息** ，这些信息通常并不关键，或对网站本身来说是次要的。
			- 为了 **SEO** 的目的， **footer** 有时也会包含一些 **常用内容** 的快速访问链接。
			- ![sample-website.png](../assets/sample-website_1701269294262_0.png)
			- [图片来源(MDN)](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Document_and_website_structure/sample-website.png)
	- ### 争议
		- 有人认为 **navigation bar** 应该是 **header** 的一部分，而不是一个单独的组件。
		- 而有些人认为，为了 **accessibility** 最好将两者区分开（这样 **screen reader** 就可以区分开两者）。
- ## 页面布局标签
	- **header** : `<header>`
	- **navigation bar** : `<nav>`
	- **main content** : `<main>`
		- **常用子节点** : `<article>` `<section>` `<div>`
	- **sidebar** : `<aside>`
		- 通常被放在 `<main>` 中。
	- **footer** : `<footer>`
	- **代码示例：**
	- ```html
	  <!DOCTYPE html>
	  <html lang="en-US">
	  <head>
	    <meta charset="utf-8" />
	    <meta name="viewport" content="width=device-width" />
	  
	    <title>My page title</title>
	    <link
	      href="https://fonts.googleapis.com/css?family=Open+Sans+Condensed:300|Sonsie+One"
	      rel="stylesheet" />
	    <link rel="stylesheet" href="style.css" />
	  </head>
	  
	  <body>
	    <!-- Here is our main header that is used across all the pages of our website -->
	  
	    <header>
	      <h1>Header</h1>
	    </header>
	  
	    <nav>
	      <ul>
	        <li><a href="#">Home</a></li>
	        <li><a href="#">Our team</a></li>
	        <li><a href="#">Projects</a></li>
	        <li><a href="#">Contact</a></li>
	      </ul>
	  
	      <!-- A Search form is another common non-linear way to navigate through a website. -->
	  
	      <form>
	        <input type="search" name="q" placeholder="Search query" />
	        <input type="submit" value="Go!" />
	      </form>
	    </nav>
	  
	    <!-- Here is our page's main content -->
	    <main>
	      <!-- It contains an article -->
	      <article>
	        <h2>Article heading</h2>
	  
	        <p>
	          Lorem ipsum dolor sit amet, consectetur adipisicing elit. Donec a diam
	          lectus. Set sit amet ipsum mauris. Maecenas congue ligula as quam
	          viverra nec consectetur ant hendrerit. Donec et mollis dolor. Praesent
	          et diam eget libero egestas mattis sit amet vitae augue. Nam tincidunt
	          congue enim, ut porta lorem lacinia consectetur.
	        </p>
	  
	        <h3>Subsection</h3>
	  
	        <p>
	          Donec ut librero sed accu vehicula ultricies a non tortor. Lorem ipsum
	          dolor sit amet, consectetur adipisicing elit. Aenean ut gravida lorem.
	          Ut turpis felis, pulvinar a semper sed, adipiscing id dolor.
	        </p>
	  
	        <p>
	          Pelientesque auctor nisi id magna consequat sagittis. Curabitur
	          dapibus, enim sit amet elit pharetra tincidunt feugiat nist imperdiet.
	          Ut convallis libero in urna ultrices accumsan. Donec sed odio eros.
	        </p>
	  
	        <h3>Another subsection</h3>
	  
	        <p>
	          Donec viverra mi quis quam pulvinar at malesuada arcu rhoncus. Cum
	          soclis natoque penatibus et manis dis parturient montes, nascetur
	          ridiculus mus. In rutrum accumsan ultricies. Mauris vitae nisi at sem
	          facilisis semper ac in est.
	        </p>
	  
	        <p>
	          Vivamus fermentum semper porta. Nunc diam velit, adipscing ut
	          tristique vitae sagittis vel odio. Maecenas convallis ullamcorper
	          ultricied. Curabitur ornare, ligula semper consectetur sagittis, nisi
	          diam iaculis velit, is fringille sem nunc vet mi.
	        </p>
	      </article>
	  
	      <!-- the aside content can also be nested within the main content -->
	      <aside>
	        <h2>Related</h2>
	  
	        <ul>
	          <li><a href="#">Oh I do like to be beside the seaside</a></li>
	          <li><a href="#">Oh I do like to be beside the sea</a></li>
	          <li><a href="#">Although in the North of England</a></li>
	          <li><a href="#">It never stops raining</a></li>
	          <li><a href="#">Oh well…</a></li>
	        </ul>
	      </aside>
	    </main>
	  
	    <!-- And here is our main footer that is used across all the pages of our website -->
	  
	    <footer>
	      <p>©Copyright 2050 by nobody. All rights reversed.</p>
	    </footer>
	  </body>
	  </html>
	  ```
- ## 页面布局标签细节
	- ### 语义化标签
		- #### `<main>`
			- 表示页面中唯一的内容。
			- 一个页面中只能有一个 `<main>` 。
			- 直接放在 `<body>` 标签中，理想情况下不能被嵌套在其他标签中。
		- #### `<article>`
			- 去掉页面的其他部分 本身就有含义的内容 (如一篇博客) 。
		- #### `<section>`
			- 页面中若干个小的单独的部分组成的功能部分 (如： 迷你地图、文章标题和摘要的组合等)
			- **最佳实践：**
				- 每一个`<section>` 最好包裹一个 `<hn>` 标签 (利于SEO)。
				- ```html
				  <section>
				    <h2>Heading</h2>
				    <p>Bunch of awesome content</p>
				  </section>
				  ```
				- 如果有如一组控制按钮这样的部分，加上 **标题** 可能影响美观，可以将其隐藏。
				- ```html
				  <section>
				    <h2 class="hidden">Controls</h2>
				    <button class="reply">Reply</button>
				    <button class="reply-all">Reply to all</button>
				    <button class="fwd">Forward</button>
				    <button class="del">Delete</button>
				  </section>
				  ```
			- 根据具体情况， `<article>` 可以分成若干个`<section>` ; `<section>` 也可以分成若干个`<article>` 。
		- #### `<aside>`
			- 包含与主要信息无直接关系或有间接关系的内容 (如 **词汇表** **作者简介** **相关链接** 等)
		- #### `<header>`
			- 表示一组介绍性的内容。
			- 作为 `<body>` 的子标签时，表示整个网页的标题; 作为 `<article>` 或 `<section>` 的子标签，则表示那个部分的标题。
		- #### `<nav>`
			- 包含网页的主要链接。
			- 一些不重要的或者次要的链接不要放在导航栏中。
		- #### `<footer>`
			- 表示页面的 **结束内容** 。
	- ### 非语义化标签
		- 如果确实找不到合适的语义化的词，只是想对内容加一些CSS或JS，应该考虑 **非语义化标签**
		- #### `<span>`
			- 行内 **非语义标签** 。
			- ```html
			  <p>
			  The King walked drunkenly back to his room at 01:00, the beer doing nothing to
			  aid him as he staggered through the door
			  <span class="editor-note">
			    [Editor's note: At this point in the play, the lights should be down low]
			  </span>.
			  </p>
			  ```
		- #### `<div>`
			- 块级 **非语义标签** 。
			- 如下这样一个 **购物车** 的组件，我们希望可以在任何界面打开它:
				- 由于它与页面的主要内容没有必然的联系，所以不能用 `<aside>` 。
				- 由于它不属于页面的主要内容，所以不能用 `<section>` 。
				- 所以，非语义化的 `<div>` 就很适合；
			- 这里我们加上 `<hn>` 标签，以帮助 **screen reader** 用户找到它。
			- ```html
			  <div class="shopping-cart">
			  <h2>Shopping cart</h2>
			  <ul>
			    <li>
			      <p>
			        <a href=""><strong>Silver earrings</strong></a>:
			        $99.95.
			      </p>
			      <img src="../products/3333-0985/thumb.png" alt="Silver earrings" />
			    </li>
			    <li>…</li>
			  </ul>
			  <p>Total cost: $237.89</p>
			  </div>
			  ```
	- ### 换行符与水平线
		- #### `<br>`
			- line break 换行符
			- 用于换行
		- #### `<hr>`
			- horizontal rule 水平线
			- 常用在主题变更时
- ## 设计一个网站
	- 在你设计出了一个 **简单网页的结构** 之后，你就需要开始设计 **整个网站应该放什么内容** 、 **需要哪些页面** 、 **页面之间如何跳转能使用户体验最好** 。
	- 这个过程被叫做 [Information architecture](https://developer.mozilla.org/en-US/docs/Glossary/Information_architecture) ，在设计一个大型网站时，实际上我们大部分时间都花在这个过程。
	- ### 1、列出公共元素
		- 列出大部分页面需要的公共元素，如 `<header>` 、 `<footer>` 等。
		- ![common-features.png](../assets/common-features_1701570040801_0.png)
		- [图片来源](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Document_and_website_structure/common-features.png)
	- ### 2、画草图
		- 画草图，大致确定你的页面有哪些块。
		- ![site-structure.png](../assets/site-structure_1701570197692_0.png)
		- [图片来源](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Document_and_website_structure/site-structure.png)
	- ### 3、内容列表
		- 头脑风暴，思考你的整个网站都具体需要什么内容（不分类，想到就列出），写一个长清单。
		- ![feature-list.png](../assets/feature-list_1701570257519_0.png)
		- [图片地址](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Document_and_website_structure/feature-list.png)
	- ### 4、内容分组
		- 将上一步得到的内容进行 **分组** ，分到不同的页面中。
		- 这个过程与这个技术很相似： [Card sorting](https://developer.mozilla.org/en-US/docs/Glossary/Card_sorting)
		- ![card-sorting.png](../assets/card-sorting_1701570403197_0.png)
		- [图片来源](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Document_and_website_structure/card-sorting.png)
	- ### 5、网站地图
		- 画一张粗略的网站地图，各个页面使用圆圈圈住，使用线条连接不同页面，以呈现网站主要的工作流。
		- 主页在中间，他可以连接大部分其他页面。
		- 大部分其他页面，应该可以从主页直接跳转（虽然有例外）。
		- ![site-map.png](../assets/site-map_1701571360790_0.png)
		- [图片地址](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Document_and_website_structure/site-map.png)
- ---
- ## 参考
	- MDN : [Document_and_website_structure](https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Document_and_website_structure)
	  logseq.order-list-type:: number