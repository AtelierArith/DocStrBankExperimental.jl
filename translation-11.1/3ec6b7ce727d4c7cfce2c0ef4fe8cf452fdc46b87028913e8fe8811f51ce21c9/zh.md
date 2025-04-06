```
mergewith!(combine, d::AbstractDict, others::AbstractDict...) -> d
mergewith!(combine)
merge!(combine, d::AbstractDict, others::AbstractDict...) -> d
```

使用其他集合中的对来更新集合。具有相同键的值将使用组合函数进行组合。柯里化形式 `mergewith!(combine)` 返回函数 `(args...) -> mergewith!(combine, args...)`。

方法 `merge!(combine::Union{Function,Type}, args...)` 作为 `mergewith!(combine, args...)` 的别名仍然可用，以保持向后兼容性。

!!! compat "Julia 1.5"
    `mergewith!` 需要 Julia 1.5 或更高版本。


# 示例

```jldoctest
julia> d1 = Dict(1 => 2, 3 => 4);

julia> d2 = Dict(1 => 4, 4 => 5);

julia> mergewith!(+, d1, d2);

julia> d1
Dict{Int64, Int64} with 3 entries:
  4 => 5
  3 => 4
  1 => 6

julia> mergewith!(-, d1, d1);

julia> d1
Dict{Int64, Int64} with 3 entries:
  4 => 0
  3 => 0
  1 => 0

julia> foldl(mergewith!(+), [d1, d2]; init=Dict{Int64, Int64}())
Dict{Int64, Int64} with 3 entries:
  4 => 5
  3 => 0
  1 => 4
```
