tags:: [[Redis]]
---

- ## Redis 产品
	- ### Redis 本身
		- #### Redis Open Source 与 Redis Enterprise Software
			- `Redis Open Source` (旧称: `Redis Community Edition` )
				- 即 Redis 开源版本.
			- `Redis Enterprise Software` / `Redis Software`
				- 即 Redis 企业版本.
			- 二者区别 (DeepSeek 总结) :
				- | **维度** | **Redis Open Source** | **Redis Enterprise Software** |
				  | ---- | ---- | ---- |
				  | 核心功能 | 基础缓存与数据结构 | 企业级扩展功能（集群、安全、模块等） |
				  | 许可类型 | 源代码可用（SSPLv1 + RSALv2） | 商业闭源许可 |
				  | 成本 | 免费（云托管可能需额外费用） | 订阅制付费 |
		- #### Redis Open Source 协议变更
			- 参考: [Redis Adopts Dual Source-Available Licensing](https://redis.io/blog/redis-adopts-dual-source-available-licensing/)
			- 从 Redis 7.4 版本开始, Redis 采用 [Redis Source Available License (RSALv2)](https://redis.io/legal/rsalv2-agreement/) 和 [Server Side Public License (SSPLv1)](https://redis.io/legal/server-side-public-license-sspl/) 双协议.
			  logseq.order-list-type:: number
			- 此变更会影响谁?
			  logseq.order-list-type:: number
				- 受影响的只有: 提供 Redis 竞品 (competitive offerings) 的组织.
					- “competitive offerings” 是指源自 Redis 代码库, 与 Redis 商业产品的功能有显著重叠, 并销售给第三方的产品.
				- 因此, 托管 Redis 产品的云厂商, 将不再被允许免费使用 Redis 源代码.
				- 但, 允许在组织内部托管 Redis , 供组织内部使用.
			- Redis 7.2 及其之前的版本将被称为 `Redis OSS` , Redis 7.4 及其之后的版本将被称为 `Redis Community Edition` (后改称为 `Redis Open Source` ).
			  logseq.order-list-type:: number
	- ### Redis Stack
	- ### Redis Cloud
	-
	- ### AI 相关产品
		- [[Redis for AI]]
			- 基于 Redis 向量数据库集成的功能和服务包, 用于开发 AI 应用.
		- [[Redis LangCache]]
			- 通过 语义缓存 (semantic caching) , 降低延迟和 LLM 调用成本.
	-