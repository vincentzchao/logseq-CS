tags:: [[JAR]]
---

- ## JAR 是啥
	- `JAR` 即 `Java ARchive` , 基于 ZIP 格式的一种 Archive 格式。
	- `JAR` 本质上，就是包含可选的 `META-INF` 目录的 ZIP 文件。
	- `JAR` 文件可以通过 `jar` 命令行或 [java.util.jar](https://docs.oracle.com/javase/8/docs/api/java/util/jar/package-summary.html) API 创建。
- ## JAR 文件的作用
	- 安全 (校验签名)
	  logseq.order-list-type:: number
	- 减少下载时间 (与多文件相比，可以只进行一次网络请求，下载一个文件)
	  logseq.order-list-type:: number
	- 压缩体积
	  logseq.order-list-type:: number
	- 可以将软件打包为 *extensions* 
	  logseq.order-list-type:: number
	- 封装 (将所有所需文件放在同一 JAR 文件中)
	  logseq.order-list-type:: number
	- 版本管理 (包含供应商和版本信息)
	  logseq.order-list-type:: number
	- 可移植性 (JAR 的处理机制是 Java 平台的规范)
	  logseq.order-list-type:: number
- ## META-INF 目录
	- META-INF 目录可能包含一下文件或目录
		- ``` sh
		  MANIFEST.MF
		  INDEX.LIST
		  x.SF
		  x.DSA
		  services/
		  ```
	- ### MANIFEST.MF
		- manifest 文件, 定义相关数据。
	- ### INDEX.LIST
		- 包含包的位置信息，以提高类加载器加载速度。
	- ### x.SF
		- JAR 文件的 **签名文件** ( `Signature File` ), `x` 为 `JAR` 文件名称 (不包含后缀) .
		- 内容是 JAR 包中所有文件的摘要.
	- ### x.DSA
		- `x.SF` 文件所关联的 **签名块文件** ( `Signature Block File` ), `x` 为 `JAR` 文件名称 (不包含后缀) .
		- DSA, 即 `Digital Signature Algorithm (数字签名算法)` .
		- (包含 签名者的数字证书 (类似 SSL 证书) 和 对 `x.SF` 文件的签名 ) .
		- `x.SF` 和 `x.DSA` 用于验证 JAR 是否被篡改.
	- ### services/
		- 存储所有 `service provider` 的配置文件.
	-
-
- ## 参考
	- [JAR File Overview](https://docs.oracle.com/javase/8/docs/technotes/guides/jar/jarGuide.html)
	  logseq.order-list-type:: number
	- [JAR File Specification](https://docs.oracle.com/javase/8/docs/technotes/guides/jar/jar.html)
	  logseq.order-list-type:: number
	- [Lesson: Packaging Programs in JAR Files](https://docs.oracle.com/javase/tutorial/deployment/jar/)
	  logseq.order-list-type:: number
	-