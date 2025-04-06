```
begin
```

`begin...end` 表示一段代码块。

```julia
begin
    println("Hello, ")
    println("World!")
end
```

通常情况下，`begin` 是不必要的，因为像 [`function`](@ref) 和 [`let`](@ref) 这样的关键字会隐式地开始代码块。另见 [`;`](@ref)。

`begin` 也可以在索引时使用，表示集合的第一个索引或数组某个维度的第一个索引。例如，`a[begin]` 是数组 `a` 的第一个元素。

!!! compat "Julia 1.4"
    将 `begin` 作为索引的使用需要 Julia 1.4 或更高版本。


# 示例

```jldoctest
julia> A = [1 2; 3 4]
2×2 Array{Int64,2}:
 1  2
 3  4

julia> A[begin, :]
2-element Array{Int64,1}:
 1
 2
```
