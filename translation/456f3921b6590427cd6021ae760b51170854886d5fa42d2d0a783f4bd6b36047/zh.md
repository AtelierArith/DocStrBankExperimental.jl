```
last(coll)
```

获取有序集合的最后一个元素，如果可以在 O(1) 时间内计算。这是通过调用 [`lastindex`](@ref) 来获取最后一个索引来实现的。即使 [`AbstractRange`](@ref) 为空，也返回其终点。

另见 [`first`](@ref), [`endswith`](@ref).

# 示例

```jldoctest
julia> last(1:2:10)
9

julia> last([1; 2; 3; 4])
4
```
