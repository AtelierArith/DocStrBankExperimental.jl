```
Base.datatype_pointerfree(dt::DataType) -> Bool
```

返回此类型的实例是否可以包含对 gc 管理内存的引用。可以在任何 `isconcretetype` 上调用。
