```
in!(x, s::AbstractSet) -> Bool
```

如果 `x` 在 `s` 中，返回 `true`。如果不在，则将 `x` 推入 `s` 并返回 `false`。这等价于 `in(x, s) ? true : (push!(s, x); false)`，但可能有更高效的实现。

另请参见: [`in`](@ref), [`push!`](@ref), [`Set`](@ref)

!!! compat "Julia 1.11"
    此函数至少需要 1.11。


# 示例

```jldoctest; filter = r"^  [1234]$"
julia> s = Set{Any}([1, 2, 3]); in!(4, s)
false

julia> length(s)
4

julia> in!(0x04, s)
true

julia> s
Set{Any} with 4 elements:
  4
  2
  3
  1
```
