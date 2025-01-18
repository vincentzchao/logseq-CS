tags:: [[Quartz]]
---

- ## 定义 Job
	- ``` java
	  public class FooJob implements Job {
	  	@Override
	  	public void execute(JobExecutionContext context) throws JobExecutionException {
	  		System.out.println("Hello World!");
	  	}
	  }
	  ```
	- 实现 `Job` 类，重写 `execute(...)` 方法就可以定义一个定时任务。
		- `execute()` 方法的参数 `JobExecutionContext` ，是 `Job` 执行的上下文信息。
- ## 创建 JobDetail 实例
	- ``` java
	  JobDetail job = JobBuilder.newJob(FooJob.class)
	    .withIdentity("job1", "group1")
	    .build();
	  
	  // 省略 创建 Trigger 实例
	  
	  // 设置创建的 JobDetail 和 Trigger
	  scheduler.scheduleJob(job, trigger);
	  ```
	- 实际被添加到 `Scheduler` 中的是 `JobDetail` 实例，创建 `JobDetail` 实例时只传入了 `Job` 的 class 。
- ## 执行 Job 时会创建 Job 实例
	- `Scheduler` 每次执行 Job 时，都会创建一个 `Job` 实例，执行它的 `executer(...)` 方法。
	- `Scheduler` 每次执行完 Job 后，创建的这个新实例都会被丢弃，等待垃圾回收。
		- 因此自定义的 Job 类应该是无状态的，只定义执行的逻辑。
	- `Scheduler` 执行  Job 时，使用 `JobFactory` 来创建 Job 实例。
		- `JobFactory` 的默认实现 `SimpleJobFactory` ，就是直接调用 `jobClass.newInstance();` 创建 `Job` 的实例，所以要求 `Job` 必须有一个无参的构造方法。
- ## 使用 JobBuilder 设置 JobDetail 属性
	- ### JobKey
		- JobDetail 可以设置 `name` 和 `group` 。
		- `name` 和 `group` 的组合，是一个 Job 的唯一标识，被称为 `JobKey` 。
		- 若未显式设置，则执行 `build()` 会设置默认值。
		- ``` java
		  // 设置 key 和 group
		  JobDetail job = JobBuilder.newJob(FooJob.class)
		    .withIdentity("job1", "group1")
		    .build();
		  ```
	- ### JobDataMap
		- #### 设置参数
			- JobDetail 可以设置 *键值对类型* 的参数，用于 Job 运行时获取。
			- 这些参数被称为 `JobDataMap` 。
			- 设置 String 和 基本数据类型的包装类型 的参数
				- ``` java
				  // 一条条参数配置
				  JobDetail job = JobBuilder.newJob(BarJob.class)
				    .withIdentity("job1", "group1")
				    .usingJobData("name", "vincent")
				    .usingJobData("age", 35)
				    .usingJobData("balance", 100.23)
				    .build();
				  ```
			- 设置自定义类型的参数：
				- ``` java
				  // 可以直接设置 JobDataMap
				  JobDataMap jobDataMap = new JobDataMap();
				  jobDataMap.put("account", new Account("vincent", 35, 100.23));
				  
				  JobDetail job = JobBuilder.newJob(BarJob.class)
				    .withIdentity("job1", "group1")
				    .usingJobData(jobDataMap)
				    .build();
				  ```
				- 需要先创建 `JobDataMap` 实例，再设置自定义类型的参数。
				- 如果要序列化存储  `JobDataMap` ，需要特别注意，修改自定义类型的属性，可能带来的序列化和反序列化问题。
		- #### 获取参数
			- 在 Job 中，可以通过 `JobExecutionContext` 取到这些参数。
			- ``` java
			  public class BarJob implements Job {
			  	@Override
			  	public void execute(JobExecutionContext context) throws JobExecutionException {
			  		JobDataMap jobDataMap = context.getJobDetail().getJobDataMap();
			  		System.out.printf("BarJob! [name = %s, age = %s, balance = %s]%n", jobDataMap.get("name"),
			  				jobDataMap.get("age"), jobDataMap.get("balance"));
			  	}
			  }
			  ```
		-
- ## 参考
	- Tutorials：
	  logseq.order-list-type:: number
		- [Lesson 2: The Quartz API, and Introduction to Jobs And Triggers](https://www.quartz-scheduler.org/documentation/quartz-2.3.0/tutorials/tutorial-lesson-02.html)
		  logseq.order-list-type:: number
		- [Lesson 3: More About Jobs & JobDetails](https://www.quartz-scheduler.org/documentation/quartz-2.3.0/tutorials/tutorial-lesson-03.html)
		  logseq.order-list-type:: number
	-
-