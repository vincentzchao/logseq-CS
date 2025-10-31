tags:: [[Flutter Widget]]
---

- ## Everything Is A Widget
	- Flutter 中 , **万物皆组件** .
	- 组件之间基于 **组合 (composition)** 形成 **层次结构 (hierarchy)** .
		- 每个组件都嵌套在其父组件内, 并可以从父组件接收 **上下文 (context)** .
- ## Build a widget
	- ### Widget State
		- Flutter 中有两种组件:
			- `StatelessWidget` : 无状态组件, 即其没有随时间变化的 `class` 属性.
			  logseq.order-list-type:: number
				- 如 `Padding` ,  `Text` 和 `Icon` .
				- 我们大多数创建的也是这类组件.
			- `StatefulWidget` : 有状态组件, 即其有随时间变化的 `class` 属性.
			  logseq.order-list-type:: number
	- ### Build a StatelessWidget
		- 创建一个 无状态组件 , 我们需要:
			- 继承 `StatelessWidget` .
			  logseq.order-list-type:: number
			- 要实现 `build()` 方法 , 返回一个 `Widget` 对象.
			  logseq.order-list-type:: number
		- ``` dart
		  class PaddedText extends StatelessWidget {
		    const PaddedText({super.key});
		  
		    @override
		    Widget build(BuildContext context) {
		      return Padding(
		        padding: const EdgeInsets.all(8.0),
		        child: const Text('Hello, World!'),
		      );
		    }
		  }
		  ```
	- ### Build a StatefulWidget
		- 创建一个 有状态组件 , 我们需要:
			- 继承 `StatefulWidget` .
			  logseq.order-list-type:: number
			- 实现 `createState()` 方法, 返回一个继承自 `State<T>` 的对象.
			  logseq.order-list-type:: number
			- 继承自 `State<T>` 的类, 需要实现 `build()` 方法 , 返回一个 `Widget` 对象.
			  logseq.order-list-type:: number
		- 每当我们修改 `State<T>` 对象的属性时, 我们都应该调用 `setState()` 方法, 以通知框架再次调用 `State` 的 `build` 方法来更新用户界面.
		- ``` dart
		  class CounterWidget extends StatefulWidget {
		    @override
		    State<CounterWidget> createState() => _CounterWidgetState();
		  }
		  
		  class _CounterWidgetState extends State<CounterWidget> {
		    int _counter = 0;
		  
		    void _incrementCounter() {
		      setState(() {
		        _counter++;
		      });
		    }
		  
		    @override
		    Widget build(BuildContext context) {
		      return Text('$_counter');
		    }
		  }
		  ```
	- ### 总结
		- 不管是 `StatelessWidget` 还是 `StatefulWidget` , 最终渲染用户界面时, 都要调用 `build()` 方法.
-
- ## 参考
	- [Flutter Docs - Widgets](https://docs.flutter.dev/get-started/fundamentals/widgets)
	  logseq.order-list-type:: number
	- logseq.order-list-type:: number