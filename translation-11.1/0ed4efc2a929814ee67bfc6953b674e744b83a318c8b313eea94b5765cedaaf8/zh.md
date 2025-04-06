```
map!(f, values(dict::AbstractDict))
```

通过将每个值从 `val` 转换为 `f(val)` 来修改 `dict`。请注意，`dict` 的类型不能更改：如果 `f(val)` 不是 `dict` 的值类型的实例，则它将尽可能转换为值类型，否则将引发错误。

!!! compat "Julia 1.2"
    `map!(f, values(dict::AbstractDict))` 需要 Julia 1.2 或更高版本。


# 示例

```jldoctest
julia> d = Dict(:a => 1, :b => 2)
Dict{Symbol, Int64} with 2 entries:
  :a => 1
  :b => 2

julia> map!(v -> v-1, values(d))
ValueIterator for a Dict{Symbol, Int64} with 2 entries. Values:
  0
  1
```
