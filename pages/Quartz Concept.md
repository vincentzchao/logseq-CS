tags:: [[Quartz]]
---

- ## 官方文档咋用
	- [Quartz 2.3.0 Documentation](https://www.quartz-scheduler.org/documentation/quartz-2.3.0/)
	- ![image.png](../assets/image_1737165473345_0.png){:height 240, :width 696}
	- 学习顺序：
		- Quick Start Guide
		  logseq.order-list-type:: number
		- Tutorials
		  logseq.order-list-type:: number
		- Examples
		  logseq.order-list-type:: number
		- Cookbook (一些 How-to)
		  logseq.order-list-type:: number
		- Configuration 和 JavaDoc 需要时查阅。
		  logseq.order-list-type:: number
- ## Quartz 是什么
	- `Quartz` 原意为 `石英` 。
	- `Quartz` 是一个定时任务框架。
- ## Hello World
	- ### 1、引入依赖
		- ``` xml
		      <dependencies>
		          <dependency>
		              <groupId>org.quartz-scheduler</groupId>
		              <artifactId>quartz</artifactId>
		              <version>2.3.0</version>
		          </dependency>
		  
		          <!-- 打印日志需要 -->
		          <dependency>
		              <groupId>org.slf4j</groupId>
		              <artifactId>slf4j-log4j12</artifactId>
		              <version>1.7.7</version>
		          </dependency>
		          <dependency>
		              <groupId>log4j</groupId>
		              <artifactId>log4j</artifactId>
		              <version>1.2.16</version>
		          </dependency>
		      </dependencies>
		  ```
		- 日志依赖的版本，来自 [quartz-2.3.0-distribution.tar.gz](https://www.quartz-scheduler.org/downloads/) 解压后 lib 目录下的依赖。
		- 如果不引入日志依赖，会报如下错误：
			- ``` sh
			  SLF4J: Failed to load class "org.slf4j.impl.StaticLoggerBinder".
			  SLF4J: Defaulting to no-operation (NOP) logger implementation
			  SLF4J: See http://www.slf4j.org/codes.html#StaticLoggerBinder for further details.
			  ```
	- ### 2、创建 log4j 配置文件
		- log4j  日志配置文件: `log4j.xml`
			- ``` xml
			  <?xml version="1.0" encoding="UTF-8"?>
			  <!DOCTYPE log4j:configuration SYSTEM "log4j.dtd">
			  
			  <log4j:configuration xmlns:log4j="http://jakarta.apache.org/log4j/">
			  
			    <appender name="default" class="org.apache.log4j.ConsoleAppender">
			      <param name="target" value="System.out"/>
			      <layout class="org.apache.log4j.PatternLayout">
			        <param name="ConversionPattern" value="[%p] %d{dd MMM hh:mm:ss.SSS aa} %t [%c]%n%m%n%n"/>
			      </layout>
			    </appender>
			  
			  
			   <logger name="org.quartz">
			     <level value="info" />
			   </logger>
			  
			    <root>
			      <level value="info" />
			      <appender-ref ref="default" />
			    </root>
			  
			    
			  </log4j:configuration>
			  ```
		- 这个配置取自 [[Quartz Examples]] 的 `example1` 中的日志配置。
		- 没有这个配置文件，运行会爆出警告，且看不到日志：
			- ``` sh
			  log4j:WARN No appenders could be found for logger (org.quartz.impl.StdSchedulerFactory).
			  log4j:WARN Please initialize the log4j system properly.
			  log4j:WARN See http://logging.apache.org/log4j/1.2/faq.html#noconfig for more info.
			  ```
	- ### 3、执行代码
		- ``` java
		  // HelloJob.java
		  public class HelloJob implements Job {
		  	private static Logger _log = LoggerFactory.getLogger(HelloJob.class);
		  
		  	public HelloJob() {
		  	}
		      
		      @Override
		  	public void execute(JobExecutionContext context)
		  			throws JobExecutionException {
		  
		  		// Say Hello to the World and display the date/time
		  		_log.info("Hello World! - " + new Date());
		  	}
		  }
		  
		  // QuartzTest.java
		  public class QuartzTest {
		  
		  	public static void main(String[] args) {
		  
		  		try {
		  			// Grab the Scheduler instance from the Factory
		  			Scheduler scheduler = StdSchedulerFactory.getDefaultScheduler();
		  
		  			// and start it off
		  			scheduler.start();
		  
		  			// define the job and tie it to our HelloJob class
		  			JobDetail job = newJob(HelloJob.class)
		  					.withIdentity("job1", "group1")
		  					.build();
		  
		  			// Trigger the job to run now, and then repeat every 40 seconds
		  			Trigger trigger = newTrigger()
		  					.withIdentity("trigger1", "group1")
		  					.startNow()
		  					.withSchedule(simpleSchedule()
		  							.withIntervalInSeconds(40)
		  							.repeatForever())
		  					.build();
		  
		  			// Tell quartz to schedule the job using our trigger
		  			scheduler.scheduleJob(job, trigger);
		  
		              // shutdown
		  			// scheduler.shutdown();
		  
		  		} catch (SchedulerException se) {
		  			se.printStackTrace();
		  		}
		  	}
		  }
		  ```
		- 上述代码会 每40s 执行一次 `Hello World` 的日志打印。
- ## 如何创建定时任务
	- ### 几个重要概念
		- `Scheduler`: 调度器，用于执行任务。
		  logseq.order-list-type:: number
			- `SchedulerFactory` : 用于创建 `Scheduler` 实例。
			  logseq.order-list-type:: number
		- `Job` :  由用户实现的、希望被 `Scheduler` 执行的任务。
		  logseq.order-list-type:: number
		- `JobDetail` : 用于定义 `Job`的一些属性，创建时需要关联 `Job` 的 class 对象。
		  logseq.order-list-type:: number
			- `JobBuilder` : 用于定义和创建 `JobDetail` 实例 。
			  logseq.order-list-type:: number
			  id:: 678b7bc9-14f6-4917-b143-32596e41c833
		- `Trigger` : 定义 `Job` 的执行时间表 (即 Schedule) 。
		  logseq.order-list-type:: number
			- `TriggerBuilder` : 用于定义和创建 `Trigger` 实例。
			  logseq.order-list-type:: number
	- ### 创建步骤
		- 通过 `SchedulerFactory` 创建一个 `Scheduler` 实例。
		  logseq.order-list-type:: number
		- 通过实现 `Job` 接口，重写 `execute()` 方法，自定义一个 `Job` 类
		  logseq.order-list-type:: number
		- 通过 `JobBuilder` ，传入自定义 `Job` 类的 class ，设置 `JobDetail` 的属性，从而创建一个 `JobDetail` 实例。
		  logseq.order-list-type:: number
		- 通过 `TriggerBuilder` ，设置一些属性 (包括 定时相关参数)，创建 `Trigger` 实例。
		  logseq.order-list-type:: number
		- 将 `JobDetail` 实例 和 `Trigger` 实例传给 `Scheduler` 实例。
		  logseq.order-list-type:: number
			- ``` java
			  scheduler.scheduleJob(job, trigger);
			  ```
		- 启动 `Scheduler` 实例。
		  logseq.order-list-type:: number
			- ``` java
			  scheduler.start();
			  ```
			- 执行 `scheduler.shutdown();` 可以进行关闭。
- ## SchedulerFactory 与 Scheduler
	- ### SchedulerFactory
		- 使用 `SchedulerFactory` 可以创建一个 `Scheduler` 实例。
		- `org.quartz.SchedulerFactory` 是一个接口，它有多种实现。
	- ### Scheduler
		- `Scheduler` 启动之后，有三种状态：
			- Started
			  logseq.order-list-type:: number
			- Stand-by Mode
			  logseq.order-list-type:: number
			- Shutdown
			  logseq.order-list-type:: number
		- 一旦一个 `Scheduler` 实例被 Shutdown , 它就不能重新 Start , 需要重新创建一个 `Scheduler` 实例。
- ## Job 与 Trigger
	- ### Job
		- #### 定义 Job
			- 实现 `Job` 类，重写 `execute()` 方法就可以定义一个定时任务。
				- `execute()` 方法的参数 `JobExecutionContext` : 包含 `Job` 实例的上下文信息。
		- #### 执行 Job
			- 实际被添加到 `Scheduler` 中的是 `JobDetail` 实例，创建 `JobDetail` 实例时只传入了 `Job` 的 class 。
			- `Scheduler` 每次执行 Job 时，都会创建一个 `Job` 实例，执行它的 `executer()` 方法。
			- `Scheduler` 每次执行完 Job 后，创建的这个新实例都会被丢弃，等待垃圾回收。
				- 因此自定义的 Job 类应该是无状态的，只定义执行的逻辑。
			- `Scheduler` 执行时，使用 `JobFactory` 来创建 Job 实例。
				- `JobFactory` 的默认实现 `SimpleJobFactory` ，就是直接调用 `jobClass.newInstance();` 创建 `Job` 的实例，所以要求 `Job` 必须有一个无参的构造方法。
	- ### Trigger
		- 两种常用 Trigger：
			- `SimpleTrigger`
				- 特定时间执行一次
				- 特定时间执行 N 次，每次之间有 T 时间延迟。
			- `CronTrigger`
				- 根据 Cron 表达式来执行。
				- 如 “每周五中午” 或 “每月 10 日的 10:15”
	- ### JobKey 与 TriggerKey
		- Job 和 Trigger 都分别可以设置 `key` 和 `group` 。
		- `key` 和 `group` 的组合，是一个 Job 或 Trigger 的唯一标识。
- ## 从哪里开始
	- 基本概念
		- `org.quartz.Scheduler`
		- `org.quartz.Job`
		- `org.quartz.JobDetail`
		- `org.quartz.Trigger`
	- 底层原理
		- `org.quartz.core.QuartzSchedulerThread`
		- `org.quartz.spi.JobStore`
		- `org.quartz.spi.ThreadPool`
		- `org.quartz.core.JobRunShell`
- ## 配置文件
	- `quartz.properties`
	-
-
- ## 参考
	- [Quick Start Guide](https://www.quartz-scheduler.org/documentation/quartz-2.3.0/quick-start.html)
	  logseq.order-list-type:: number
	- Tutorials：
	  logseq.order-list-type:: number
		- [Lesson 1: Using Quartz](https://www.quartz-scheduler.org/documentation/quartz-2.3.0/tutorials/tutorial-lesson-01.html)
		  logseq.order-list-type:: number
		- [Lesson 2: The Quartz API, and Introduction to Jobs And Triggers](https://www.quartz-scheduler.org/documentation/quartz-2.3.0/tutorials/tutorial-lesson-02.html)
		  logseq.order-list-type:: number
-