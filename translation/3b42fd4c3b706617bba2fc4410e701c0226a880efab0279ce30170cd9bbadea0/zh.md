```
Base.datatype_haspadding(dt::DataType) -> Bool
```

返回此类型实例的字段是否在内存中打包，没有中间的填充位（定义为其值不唯一影响应用于结构字段的相等测试的位）。可以在任何 `isconcretetype` 上调用。
