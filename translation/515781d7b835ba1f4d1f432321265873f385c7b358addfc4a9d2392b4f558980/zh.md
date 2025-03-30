```
get(f::Union{Function, Type}, collection, key)
```

返回给定键存储的值，如果该键没有映射，则返回 `f()`。 使用 [`get!`](@ref) 也可以将默认值存储在字典中。

这旨在使用 `do` 块语法调用

```julia
get(dict, key) do
    # 默认值在这里计算
    time()
end
```
