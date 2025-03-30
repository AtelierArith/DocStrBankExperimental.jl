```
collect(collection)
```

返回一个包含集合或迭代器中所有项的 `Array`。对于字典，返回一个 `key=>value` [Pair](@ref Pair) 的 `Vector`。如果参数是类数组的或是具有 [`HasShape`](@ref IteratorSize) 特性的迭代器，则结果将具有与参数相同的形状和维数。

由 [comprehensions](@ref man-comprehensions) 使用，以将 [generator expression](@ref man-generators) 转换为 `Array`。因此，在生成器上，可以使用方括号表示法，而不是调用 `collect`，见第二个示例。

# 示例

从 `UnitRange{Int64}` 集合中收集项：

```jldoctest
julia> collect(1:3)
3-element Vector{Int64}:
 1
 2
 3
```

从生成器中收集项（与 `[x^2 for x in 1:3]` 的输出相同）：

```jldoctest
julia> collect(x^2 for x in 1:3)
3-element Vector{Int64}:
 1
 4
 9
```
