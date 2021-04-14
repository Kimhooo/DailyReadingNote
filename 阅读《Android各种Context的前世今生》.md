[Android各种Context的前世今生](https://www.jianshu.com/p/c5efb41f2ef0)

四大组件，Application 和资源类都涉及到 context，通常翻译为 `上下文`，其实个人认为理解为抽象的 `环境` 比较恰当。

在分析不同 context 的应用场景和 debug 时候很实用，值得一看。

##### Application
```
在创建 Application 的时候，会先构造 ContextImpl 对象，然后构造 Application 实例。
并将 Application 里的 mBase 指向 ContextImpl 对象，最后将 ContextImpl mOuterContext 指向 app。
完成了 Application和ContextImpl 关联，也即是 ContextWrapper 和 ContextImpl 的关联。
```
