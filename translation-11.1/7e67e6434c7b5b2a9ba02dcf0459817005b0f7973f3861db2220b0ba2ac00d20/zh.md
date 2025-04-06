```
Pair(x, y)
x => y
```

构造一个类型为 `Pair{typeof(x), typeof(y)}` 的 `Pair` 对象。元素存储在 `first` 和 `second` 字段中。它们也可以通过迭代访问（但 `Pair` 在广播操作中被视为一个单一的“标量”）。

另见 [`Dict`](@ref)。

# 示例

```jldoctest
julia> p = "foo" => 7
"foo" => 7

julia> typeof(p)
Pair{String, Int64}

julia> p.first
"foo"

julia> for x in p
           println(x)
       end
foo
7

julia> replace.(["xops", "oxps"], "x" => "o")
2-element Vector{String}:
 "oops"
 "oops"
```
