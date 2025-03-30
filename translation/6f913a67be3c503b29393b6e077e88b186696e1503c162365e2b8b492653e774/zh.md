```
size(A::AbstractArray, [dim])
```

返回一个包含 `A` 维度的元组。您可以选择指定一个维度以仅获取该维度的长度。

请注意，对于具有非标准索引的数组，`size` 可能未定义，在这种情况下 [`axes`](@ref) 可能会很有用。请参阅手册中关于 [具有自定义索引的数组](@ref man-custom-indices) 的章节。

另请参见：[`length`](@ref), [`ndims`](@ref), [`eachindex`](@ref), [`sizeof`](@ref)。

# 示例

```jldoctest
julia> A = fill(1, (2,3,4));

julia> size(A)
(2, 3, 4)

julia> size(A, 2)
3
```
