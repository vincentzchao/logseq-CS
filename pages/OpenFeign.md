tags:: [[Feign]]

- ---
-
- ## 常见问题
	- ### 关于 MethodType
		- 在接口层，定义如下方法；如果 @FeignClient 标注的类继承这个接口，在执行时，会报错，因为
		- ```java
		  @RequestMapping(path = "/refreshAll", method = { RequestMethod.*GET*, RequestMethod.*POST *})
		  ```