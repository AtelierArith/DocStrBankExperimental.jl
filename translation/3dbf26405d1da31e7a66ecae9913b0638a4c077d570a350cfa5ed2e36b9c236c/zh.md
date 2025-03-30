```
Base.summarysize(obj; exclude=Union{...}, chargeall=Union{...}) -> Int
```

计算从参数可达的所有唯一对象所使用的内存量（以字节为单位）。

# 关键字参数

  * `exclude`：指定在遍历中要排除的对象类型。
  * `chargeall`：指定始终计算其所有字段大小的对象类型，即使这些字段通常会被排除。

另请参见 [`sizeof`](@ref)。

# 示例

```jldoctest
julia> Base.summarysize(1.0)
8

julia> Base.summarysize(Ref(rand(100)))
848

julia> sizeof(Ref(rand(100)))
8
```
