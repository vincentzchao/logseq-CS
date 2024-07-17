tags:: [[Hexo]]
---

- Hexo 对于 Markdown 文章中使用图片支持得不好，如果要用相对路径来引入图片，必须使用 `source/images/` 目录下的图片。
- 我们要的是，Markdown 文章中可以直接使用 *相对路径* 读取文章同名目录下的图片。
- 使用 [hexo-relative-link](https://github.com/2-3-5-7/hexo-relative-link) 插件：
	- 执行 `npm install hexo-relative-link` 安装插件。
	  logseq.order-list-type:: number
	- 在 `_config.yml` 作如下配置。
	  logseq.order-list-type:: number
		- ``` yml
		  post_asset_folder: true
		  ```
		- 这样在执行 `hexo new` 命令时，会创建同名目录用来存放图片；
		- 同时，也让 Hexo 能够读取文章同名目录下的图片。
-