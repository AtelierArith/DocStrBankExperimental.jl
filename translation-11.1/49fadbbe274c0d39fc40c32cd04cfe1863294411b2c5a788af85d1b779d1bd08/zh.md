```
Base.Pairs(values, keys) <: AbstractDict{eltype(keys), eltype(values)}
```

将一个可索引的容器转换为相同数据的字典视图。修改底层数据的键空间可能会使此对象失效。
