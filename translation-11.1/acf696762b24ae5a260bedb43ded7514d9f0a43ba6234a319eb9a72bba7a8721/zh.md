```
mergewith(combine, d::AbstractDict, others::AbstractDict...)
mergewith(combine)
merge(combine, d::AbstractDict, others::AbstractDict...)
```

从给定的集合构造一个合并的集合。如果需要，结果集合的类型将被提升以适应合并集合的类型。具有相同键的值将使用组合函数进行合并。柯里化形式 `mergewith(combine)` 返回函数 `(args...) -> mergewith(combine, args...)`。

方法 `merge(combine::Union{Function,Type}, args...)` 作为 `mergewith(combine, args...)` 的别名仍然可用，以保持向后兼容性。

!!! compat "Julia 1.5"
    `mergewith` 需要 Julia 1.5 或更高版本。


# 示例

```jldoctest
julia> a = Dict("foo" => 0.0, "bar" => 42.0)
Dict{String, Float64} with 2 entries:
  "bar" => 42.0
  "foo" => 0.0

julia> b = Dict("baz" => 17, "bar" => 4711)
Dict{String, Int64} with 2 entries:
  "bar" => 4711
  "baz" => 17

julia> mergewith(+, a, b)
Dict{String, Float64} with 3 entries:
  "bar" => 4753.0
  "baz" => 17.0
  "foo" => 0.0

julia> ans == mergewith(+)(a, b)
true
```
