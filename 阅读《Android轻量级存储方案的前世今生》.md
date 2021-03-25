[《Android轻量级存储方案的前世今生》](https://mp.weixin.qq.com/s/DNiaQEcE7LOhhxfLu7gycg)

```
每当调用 SharedPreferencesImpl 的构造器的时候，
都会开始调用 startLoadFromDisk 方法，
然后在该方法中开启一个子线程加载 xml 文件中的内容，
最后将 xml 中的内容全部加载到 mMap中。
```

sp的源码中会用一个静态的 ArrayMap 去存储用过的sp，也就是说用过的 sp 永远存在于内存中。


mmkv基于 mMap和 protobuf ，天然不存在sp的anr，跨进程问题。

mmkv的背景
```
MMKV 原本是要解决微信上特殊文字引起系统的 crash，解决过程中有一些计数器需要保存（因为闪退随时可能发生），
这时就需要一个性能非常高的通用 key-value组件
SharedPreferences、NSUserDefaults、SQLite 等常见组件这些都不满足
考虑到这个防 crash 方案最主要的诉求还是实时写入，
而 mmap 内存映射文件刚好满足这种需求。
```


想起字节团队好像有篇文章也讲了sp的缺点，忘了，有时间找找。
