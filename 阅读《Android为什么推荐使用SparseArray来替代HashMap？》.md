[Android为什么推荐使用SparseArray来替代HashMap？](https://blog.csdn.net/woshizisezise/article/details/79361458)

SparseArray，翻译过来称为“稀疏数组”，所谓稀疏数组就是数组中大部分的内容值都未被使用（或都为零），在数组中仅有少部分的空间使用。

SparseArray 比 HashMap 更省内存，在某些条件下性能更好，主要是因为它避免了对 key 的自动装箱（int 转为 Integer 类型）。

它内部则是通过两个数组来进行数据存储的，一个存储 key，另外一个存储 value。


为了**优化性能**，它内部对数据还采取了压缩的方式来表示稀疏数组的数据，从而节约内存空间。

##### 应用场景：

虽说SparseArray性能比较好，但是由于其添加、查找、删除数据都需要先进行一次二分查找，所以在数据量大的情况下性能并不明显，将降低至少50%。

满足下面两个条件我们可以使用SparseArray代替HashMap：

1. 数据量不大，最好在千级以内
2. key必须为int类型，这中情况下的HashMap可以用SparseArray代替：
```
HashMap<Integer, Object> map = new HashMap<>();
用SparseArray代替:
SparseArray<Object> array = new SparseArray<>();
 ```
