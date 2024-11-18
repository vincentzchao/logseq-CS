tags:: [[Spring Framework]], [[Spring - 面试重点]] 
---

- ## ==疑问==
	- 属性赋值阶段到底干了啥？
	  logseq.order-list-type:: number
		- 是 @Autowired 之类的注解注入属性吗？
		- 但是我看资料好像 @Autowired 是基于 AutowiredAnnotationBeanPostProcessor 实现，它实现了 BeanPostProcessor 。
	- XXXAware 接口到底什么作用？
	  logseq.order-list-type:: number
	- AOP 和 Bean 的三级缓存的关系
	  logseq.order-list-type:: number
	- 第三级缓存中的 ObjectFactory 是啥
	  logseq.order-list-type:: number
	- DefaultSingletonBeanRegistry
	  logseq.order-list-type:: number
	- BeanFactory 是啥啊
	  logseq.order-list-type:: number
-
- ## SpringApplication.run() 调用链路
	- 以下调用链路是只引用了 `spring-boot-starter` 依赖，代码只写了两个 @Component Bean 的场景：
	- main 方法调用 `SpringApplication.run(App.class, args)`
	  logseq.order-list-type:: number
	- `run`方法内部，调用 `SpringApplication` 的 `run(String... args)`
	  logseq.order-list-type:: number
	- `run`方法内部，调用 `context = createApplicationContext()` 获取 `context` 为 `AnnotationConfigApplicationContext` 的实例。
	  logseq.order-list-type:: number
		- 继承关系: `AnnotationConfigApplicationContext -> GenericApplicationContext -> AbstractApplicationContext -> ConfigurableApplicationContext(接口) -> ApplicationContext(接口)`
	- 得到 `context` 后，调用 `refreshContext(context)` , 内部调用 `context.refresh()` .
	  logseq.order-list-type:: number
	  id:: 6738b12b-28e4-4ee0-9ae6-a332aa31bdcd
		- `refresh()` 方法的实现，来自 `AbstractApplicationContext`
	- `refresh` 方法内部，`obtainFreshBeanFactory()` 获取 `beanFactory` 为 `DefaultListableBeanFactory` 的实例。
	  logseq.order-list-type:: number
		- 继承关系:
			- `DefaultListableBeanFactory -> ConfigurableListableBeanFactory(接口) -> ... -> BeanFactory(接口)`
			- `DefaultListableBeanFactory -> AbstractAutowireCapableBeanFactory -> AbstractBeanFactory -> ... -> BeanFactory(接口)`
			- `DefaultListableBeanFactory -> AbstractAutowireCapableBeanFactory -> AbstractBeanFactory -> FactoryBeanRegistrySupport -> DefaultSingletonBeanRegistry`
	- 得到 `beanFactory` 后，调用 `context` 的 `finishBeanFactoryInitialization(beanFactory)` 方法
	  logseq.order-list-type:: number
		- 该方法来自 `context` 的祖先类 `AbstractApplicationContext` 。
		- 另一方向：
			- 得到 `beanFactory` 后，调用 `context` 的 `invokeBeanFactoryPostProcessors(beanFactory)` 方法
			  logseq.order-list-type:: number
				- 该方法来自 `context` 的祖先类 `AbstractApplicationContext`
			- `invokeBeanFactoryPostProcessors` 方法内部，调用 `PostProcessorRegistrationDelegate.invokeBeanFactoryPostProcessors(beanFactory, getBeanFactoryPostProcessors())`
			  logseq.order-list-type:: number
			- `invokeBeanFactoryPostProcessors` 方法内部，调用 `beanFactory.getBean(ppName, BeanDefinitionRegistryPostProcessor.class)`
			  logseq.order-list-type:: number
				- `getBean()` 方法的实现，来自 `AbstractBeanFactory`
	- `finishBeanFactoryInitialization` 方法内部，调用 `beanFactory` 的 `preInstantiateSingletons()` 方法
	  logseq.order-list-type:: number
		- 该方法来自 `DefaultListableBeanFactory` 。
	- `preInstantiateSingletons()` 方法内部，遍历所有 beanName ，调用 `getBean()` 方法获取 Bean。
	  logseq.order-list-type:: number
		- 该方法来自 `beanFactory` 的祖先类 `AbstractBeanFactory`
	- `getBean` 方法内部，调用 `beanFactory` 的 `doGetBean(name, requiredType, null, false)` 方法。
	  logseq.order-list-type:: number
		- 该方法来自 `beanFactory` 的祖先类 `AbstractBeanFactory`
	- `doGetBean` 方法内部，先调用 `beanFactory` 的 `getSingleton(String beanName)` 方法，用于判断 bean 是否在缓存中。
	  logseq.order-list-type:: number
		- 该方法来自 `beanFactory` 的祖先类 `AbstractBeanFactory` 的祖先类 `DefaultSingletonBeanRegistry` 。
	- `doGetBean` 方法内部，调用 `beanFactory` 的 `getSingleton(String beanName, ObjectFactory<?> singletonFactory)` 方法。
	  logseq.order-list-type:: number
		- 该方法来自 `beanFactory` 的祖先类 `AbstractBeanFactory` 的祖先类 `DefaultSingletonBeanRegistry` 。
	- `getSingleton` 方法传入一个 `ObjectFactory<?>` 接口的实现类，内部调用 `ObjectFactory` 的 `getObject()` 方法，其实就是如下代码：
	  logseq.order-list-type:: number
		- ``` java
		  getSingleton(beanName, () -> {
		    try {
		      return createBean(beanName, mbd, args);
		    }
		    catch (BeansException ex) {
		      // Explicitly remove instance from singleton cache: It might have been put there
		      // eagerly by the creation process, to allow for circular reference resolution.
		      // Also remove any beans that received a temporary reference to the bean.
		      destroySingleton(beanName);
		      throw ex;
		    }
		  });
		  ```
	- `getSingleton` 方法内部其实就是调用了  `beanFactory`  的 `createBean()` 方法。
	  logseq.order-list-type:: number
		- 该方法来自 `beanFactory` 的父类 `AbstractAutowireCapableBeanFactory` 。
	- `createBean()` 方法内部调用 `AbstractAutowireCapableBeanFactory`  的 `doCreateBean()` 方法
	  logseq.order-list-type:: number
	- `doCreateBean()` 方法开始真正创建 bean 。
	  logseq.order-list-type:: number
- ## BeanPostProcessor
	- `AutowiredAnnotationBeanPostProcessor` ，用于实现  `@Autowired` 注解。
	-
- ## 三级缓存
	- ### 三级缓存就是三个 Map
		- ``` java
		  // 代码来自 org.springframework.beans.factory.support.DefaultSingletonBeanRegistry
		  // 一级缓存：bean name to bean instance
		  /** Cache of singleton objects: bean name to bean instance. */
		  private final Map<String, Object> singletonObjects = new ConcurrentHashMap<>(256);
		  
		  // 二级缓存：bean name to bean instance
		  /** Cache of early singleton objects: bean name to bean instance. */
		  private final Map<String, Object> earlySingletonObjects = new ConcurrentHashMap<>(16);
		  
		  // 三级缓存：bean name to ObjectFactory
		  /** Cache of singleton factories: bean name to ObjectFactory. */
		  private final Map<String, ObjectFactory<?>> singletonFactories = new HashMap<>(16);
		  ```
	- ### 缓存中取 Bean 的步骤
		- ``` java
		  // 来自 DefaultSingletonBeanRegistry
		  protected Object getSingleton(String beanName, boolean allowEarlyReference) {
		    // Quick check for existing instance without full singleton lock
		    Object singletonObject = this.singletonObjects.get(beanName);
		    if (singletonObject == null && isSingletonCurrentlyInCreation(beanName)) {
		      singletonObject = this.earlySingletonObjects.get(beanName);
		      if (singletonObject == null && allowEarlyReference) {
		        synchronized (this.singletonObjects) {
		          // Consistent creation of early reference within full singleton lock
		          singletonObject = this.singletonObjects.get(beanName);
		          if (singletonObject == null) {
		            singletonObject = this.earlySingletonObjects.get(beanName);
		            if (singletonObject == null) {
		              ObjectFactory<?> singletonFactory = this.singletonFactories.get(beanName);
		              if (singletonFactory != null) {
		                singletonObject = singletonFactory.getObject();
		                this.earlySingletonObjects.put(beanName, singletonObject);
		                this.singletonFactories.remove(beanName);
		              }
		            }
		          }
		        }
		      }
		    }
		    return singletonObject;
		  }
		  ```
		- 根据 beanName 从一级缓存中取 Bean 的实例：
		  logseq.order-list-type:: number
			- 取到就返回。
			  logseq.order-list-type:: number
			- 没取到就进行下一步。
			  logseq.order-list-type:: number
		- 根据 beanName 从二级缓存中取 Bean 的实例：
		  logseq.order-list-type:: number
			- 取到就返回。
			  logseq.order-list-type:: number
			- 没取到就进行下一步。
			  logseq.order-list-type:: number
		- 根据 beanName 从三级缓存中取 Bean 的 ObjectFactory ：
		  logseq.order-list-type:: number
			- 取到的话：
			  logseq.order-list-type:: number
				- 调用 ObjectFactory 的 getObject()，得到 Bean 的 **前期暴露对象** ；
				  logseq.order-list-type:: number
				- 将这个实例放到二级缓存中。
				  logseq.order-list-type:: number
				- 将三级缓存中的 ObjectFactory 移除。
				  logseq.order-list-type:: number
			- 没取到就返回 null
			  logseq.order-list-type:: number
	- ### 循环依赖的创建过程
		- ``` java
		  @Component("beanA")
		  public class BeanA {
		    @Autowired
		    private BeanB beanB;
		  }
		  
		  @Component("beanB")
		  public class BeanB {
		    @Autowired
		    private BeanA beanA;
		  }
		  ```
		- 当我们创建 `BeanA` 时，检查缓存中是否有 `BeanA` 。
		  logseq.order-list-type:: number
			- 因为还没创建，所以没有。
		- 通过反射实例化 `BeanA` 。
		  logseq.order-list-type:: number
			- 调用 `AbstractAutowireCapableBeanFactory` 的 `createBeanInstance(beanName, mbd, args)` 实例化。
		- 将 `BeanA` 的 ObjectFactory 放入三级缓存中。
		  logseq.order-list-type:: number
			- 调用的是 `DefaultSingletonBeanRegistry` 的 `addSingletonFactory(beanName, () -> getEarlyBeanReference(beanName, mbd, bean));`
		- 给 `BeanA` 注入属性时，发现需要 `BeanB` 。
		  logseq.order-list-type:: number
			- `populateBean(beanName, mbd, instanceWrapper)` 会对 @Autowired、@Resource、@Value 等注解标注的属性进行填充。
		- 检查缓存中是否有 `BeanB` 。
		  logseq.order-list-type:: number
			- 因为还没创建，所以没有。
		- 开始 `BeanB` 创建流程。
		  logseq.order-list-type:: number
			- 通过反射实例化 `BeanB` 。
			  logseq.order-list-type:: number
			- 将 `BeanB` 的 ObjectFactory 放入三级缓存中。
			  logseq.order-list-type:: number
			- 给 `BeanB` 注入属性时，发现需要 `BeanA` 。
			  logseq.order-list-type:: number
			- 检查 缓存 中是否有 `BeanA` ，得到 `BeanA` 的实例。
			  logseq.order-list-type:: number
				- 从三级缓存中得到 `BeanA` 的 ObjectFactory，调用 getObject()，得到 `BeanA` 的 **前期暴露对象** 。
				  logseq.order-list-type:: number
				- 将 `BeanA` 的实例放到 二级缓存 中。
				  logseq.order-list-type:: number
				- 将三级缓存中的 `BeanA` 的  ObjectFactory 移除。
				  logseq.order-list-type:: number
			- `BeanB` 成功注入属性 `BeanA`，`BeanB` 创建成功。
			  logseq.order-list-type:: number
			- `BeanB` 加入到一级缓存中，三级缓存中删除 `BeanB` 。
			  logseq.order-list-type:: number
				- ``` java
				  // DefaultSingletonBeanRegistry
				  protected void addSingleton(String beanName, Object singletonObject) {
				    synchronized (this.singletonObjects) {
				      this.singletonObjects.put(beanName, singletonObject);
				      this.singletonFactories.remove(beanName);
				      this.earlySingletonObjects.remove(beanName);
				      this.registeredSingletons.add(beanName);
				    }
				  }
				  ```
		- `BeanA` 成功注入属性 `BeanB`，`BeanA` 创建成功。
		  logseq.order-list-type:: number
		- `BeanA` 加入到一级缓存中，二级缓存中删除 `BeanA` 。
		  logseq.order-list-type:: number
	- ### 只用一、三级缓存行不行
		-
	- ### 三级缓存不能解决的循环依赖
		- 多实例 Bean 的循环依赖。
		  logseq.order-list-type:: number
			- 因为多实例的 Bean 不会使用缓存，不使用缓存也就无法解决循环依赖
		- 使用构造器注入。
		  logseq.order-list-type:: number
			- 因为构造器注入需要注入依赖，
	- ### 不推荐编写循环依赖代码
		- 循环依赖是一种设计缺陷，应尽量避免。
		  logseq.order-list-type:: number
		- SpringBoot 2.6.x 之后默认禁止循环依赖 ( 配置 `spring.main.allow-circular-references=true` 可以允许循环依赖 )
		  logseq.order-list-type:: number
-
- ## 参考
	- [Spring的循环依赖，学就完事了【附源码】](https://www.cnblogs.com/summerday152/p/13648377.html)
	  logseq.order-list-type:: number
	- [spring硬核知识点-spring循环依赖-三级缓存](https://www.bilibili.com/video/BV1Fa411j7kc/?vd_source=f1fbb083ddef12dcff3388779faac201)
	  logseq.order-list-type:: number
	- [华为二面：Spring是如何解决循环依赖的？为什么一定要三级缓存？二级缓存能不能解决循环依赖？](https://www.bilibili.com/video/BV19H4y1778T/?vd_source=f1fbb083ddef12dcff3388779faac201)
	  logseq.order-list-type:: number
	- logseq.order-list-type:: number