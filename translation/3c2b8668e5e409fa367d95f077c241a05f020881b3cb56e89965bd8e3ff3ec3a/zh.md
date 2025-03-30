```
Base.datatype_alignment(dt::DataType) -> Int
```

此类型实例的内存分配最小对齐。可以在任何 `isconcretetype` 上调用，尽管对于内存，它将给出元素的对齐，而不是整个对象的对齐。
