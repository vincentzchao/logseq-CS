tags:: [[MySQL]], [[Transaction]] 
---

- ## 问题点
	- 事务是什么？
	  logseq.order-list-type:: number
	- MySQL 是如何保证事务的？
	  logseq.order-list-type:: number
	- 多条查询语句加事务，会发生什么？会有什么锁吗？会导致性能下降吗？
	  logseq.order-list-type:: number
	- MySQL 与 Spring 事务？
	  logseq.order-list-type:: number
- ## 事务问题
	- ### 多个事务同时插入一条没有唯一索引的数据
		- #### 场景
			- 我有一个退款单表，关键字段有: `原订单 id` , `退款状态` ,  `退款状态`  有 `退款中` , `退款失败` ,  `退款成功` 。
			  logseq.order-list-type:: number
			- 现在我有一个订单需要退款，我们需要在退款单表里插入一条退款单数据。
			  logseq.order-list-type:: number
			- 要求是：
			  logseq.order-list-type:: number
				- 同一个订单，同一时间，只能存在一条 `退款状态` 为 `退款中` 的退款单数据 (如何保证，并发时，不会插入多条？)。
				  logseq.order-list-type:: number
				- 一个订单如果退款失败，则可以重新发起一次退款，在退款单表中插入一条新数据。
				  logseq.order-list-type:: number
		- #### 方案一
			- 在 `退款状态` 上改用固定值代替条件筛选，配合唯一索引。例如，给表添加一个额外的字段 `is_processing`，表示是否为“退款中”状态。
			- ```sql
			  ALTER TABLE refund_table ADD COLUMN is_processing TINYINT(1) NOT NULL DEFAULT 0;
			  CREATE UNIQUE INDEX unique_refund_processing ON refund_table (original_order_id, is_processing);
			  ```
			- 然后在插入数据时：
				- 如果 `退款状态` 为 `退款中`，设置 `is_processing = 1`。
				- 如果 `退款状态` 为 `退款成功` 或 `退款失败`，设置 `is_processing = 0`。
			- **优点**: 实现了逻辑上的条件唯一约束。
			- **缺点**: 需要多维护一个字段，数据设计稍复杂。
		-