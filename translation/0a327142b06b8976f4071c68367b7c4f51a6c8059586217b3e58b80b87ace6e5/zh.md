```
findnext(predicate::Function, A, i)
```

查找在 `i` 之后或包括 `i` 的 `A` 中的元素的下一个索引，该元素使得 `predicate` 返回 `true`，如果未找到则返回 `nothing`。这适用于数组、字符串以及大多数支持 [`getindex`](@ref)、[`keys(A)`](@ref) 和 [`nextind`](@ref) 的其他集合。

索引与 [`keys(A)`](@ref) 和 [`pairs(A)`](@ref) 返回的类型相同。

# 示例

```jldoctest
julia> A = [1, 4, 2, 2];

julia> findnext(isodd, A, 1)
1

julia> findnext(isodd, A, 2) # 返回 nothing，但在 REPL 中未打印

julia> A = [1 4; 2 2];

julia> findnext(isodd, A, CartesianIndex(1, 1))
CartesianIndex(1, 1)

julia> findnext(isspace, "a b c", 3)
4
```
