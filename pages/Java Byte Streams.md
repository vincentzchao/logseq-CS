tags:: [[Java IO]]
---

- ## 什么是 Byte Streams
	- 参考: [The Java™ Tutorials - Byte Streams](https://docs.oracle.com/javase/tutorial/essential/io/bytestreams.html)
	- 即 **字节流** , 程序使用 **字节流** 来执行 **字节 ( 8-bit bytes )** 的输入和输出
	- Java 中所有 `Byte Streams` 都继承自 `InputStream` and `OutputStream` .
- ## InputStream
	- 参考: [Java 8 API - InputStream](https://docs.oracle.com/javase/8/docs/api/java/io/InputStream.html)
	- ### read() 方法
		- #### 关于返回值
			- 读取输入流中的下一个字节的数据.
				- 如果有数据, 则返回 0 - 255 (将字节的 8 位视为无符号整数).
				- 如果到达 流末尾 ([[EOF]]) , 则返回 -1.
		- #### 关于阻塞
			- 当没有读到新数据, 而流又未结束时: `read` 方法会被阻塞 .
			- 发生如下情况, `read` 方法会结束阻塞:
				- 收到新数据.
				  logseq.order-list-type:: number
				- 收到 [[EOF]] (流结束) 信号.
				  logseq.order-list-type:: number
				- 发生异常.
				  logseq.order-list-type:: number
	- ### read(byte b[]) 与 read(byte b[], int off, int len) 方法
		- #### 几个 read 方法的关系
			- `read(byte b[])`  方法内部, 其实就是调用 `read(byte b[], int off, int len)` 方法:
			- 而 `read(byte b[], int off, int len)` 内部其实就是循环调用 `read()` 方法.
				- 第一次调用 `read()` 方法异常时, 会直接抛出异常.
				- 非第一次调用 `read()` 方法异常时, 会视为 [[EOF]] .
		- #### 关于阻塞
			- 由于是循环调用 `read()` 方法, 所以 `read()` 方法阻塞时, `read(byte b[], int off, int len)` 就阻塞.
				- 也即: 已读的数据未满 `len` 个字节, 当前没有读到新数据, 而流又未结束时.
			- 发生如下情况, 会结束阻塞:
				- 收到 `len` 个字节的数据.
				  logseq.order-list-type:: number
				- 收到 [[EOF]] (流结束) 信号.
				  logseq.order-list-type:: number
				- 发生异常.
				  logseq.order-list-type:: number
		- #### 实现建议
			- 循环调用 `read()` 方法每次只读一个字节的方式, 并不高效
				- 建议, 子类为 `read(byte b[], int off, int len)` 提供更高效的实现.
				- 比如, `FileInputStream` 和 `BufferedInputStream` 都重写了这个方法.
	- ### skip(long n) 方法
		- 跳过 n 个字节 (如果有这么多) , 返回实际跳过的字节数 .
		- 内部会调用 `read(byte b[], int off, int len)` 方法 (创建并传入一个 byte 数组) 来读取并跳过数据.
			- ==这种实现并不高效, 建议子类重写.==
	- ### available() 方法
		- **作用**：返回一个 **估计值**，表示接下来调用 `read/skip` 而不会发生阻塞的字节数 .
			- 这个 **估计值** ≈ **缓冲区里可以立即读取的字节数**
			- 由于是估计值, 所以后面调用 `read/skip` 发生阻塞的字节数, 可能小于这个值.
		- `InputStream` 的该方法直接返回 0, 子类需要重写.
		- ==注意, 有些实现可能会直接返回流中的所有数据的字节数, 但大多数不会.==
	- ### mark 与 reset
		- #### markSupported() 方法
			- 返回是否支持 mark 和 reset .
			- 这个值应该是每个流实例的不变属性.
		- #### mark(int readlimit) 方法
			- `mark(int readlimit)` 方法的通用约定:
				- 如果流已关闭, 则此方法无任何影响.
				- 如果流未关闭, 且 `markSupported()` 方法 返回 true , 则流会以某种方式保留调用 `mark(int readlimit)` 后读取的所有字节.
					- 如果在调用 `reset()` 方法前, 读取的字节数未超过 `readlimit`, 则应一直保留数据, 以供后续读取.
					- 如果在调用 `reset()` 方法前, 读取的字节数超过 `readlimit` , 则无需保留任何数据 (包括超过 `readlimit` 之前的数据) .
		- #### reset() 方法
			- 将此流重新定位到上次调用 `mark` 方法时的位置。
			- `reset()` 方法的通用约定:
				- 如果  `markSupported()` 方法 返回 true:
					- 如果未调用过 `mark` 方法, 可以选择抛出 `IOException` .
						- 如果未选择抛出 `IOException` , 则流被重置到流的开头 (如果支持的话)
					- 如果读取的字节数超过 `readlimit`,  也可以选择抛出 `IOException` .
						- 如果未选择抛出 `IOException` , 则流被重置到上次调用 `mark` 方法的地方.
				- 如果  `markSupported()` 方法 返回 false:
					- 可以选择抛出 `IOException` .
						- 如果未选择抛出 `IOException` , 流将被重置到某个固定状态 (这个状态时什么, 取决于具体的流的实现) .
- ## OutputStream
	- 参考: [Java 8 API - OutputStream](https://docs.oracle.com/javase/8/docs/api/java/io/OutputStream.html)
- ## 参考
	- logseq.order-list-type:: number