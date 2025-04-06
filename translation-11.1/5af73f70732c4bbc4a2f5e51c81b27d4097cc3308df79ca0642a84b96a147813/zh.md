```
contains(needle)
```

创建一个函数，检查其参数是否包含 `needle`，即一个等价于 `haystack -> contains(haystack, needle)` 的函数。

返回的函数类型为 `Base.Fix2{typeof(contains)}`，可以用来实现专门的方法。
