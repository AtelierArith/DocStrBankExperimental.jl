```
hasmethod(f, t::Type{<:Tuple}[, kwnames]; world=get_world_counter()) -> Bool
```

确定给定的泛型函数是否具有与给定的 `Tuple` 参数类型匹配的方法，并且该方法的世界年龄上限由 `world` 给出。

如果提供了一个关键字参数名称的元组 `kwnames`，这也会检查与 `t` 匹配的 `f` 的方法是否具有给定的关键字参数名称。如果匹配的方法接受可变数量的关键字参数，例如使用 `kwargs...`，则 `kwnames` 中给出的任何名称都被视为有效。否则，提供的名称必须是该方法的关键字参数的子集。

另请参见 [`applicable`](@ref)。

!!! compat "Julia 1.2"
    提供关键字参数名称需要 Julia 1.2 或更高版本。


# 示例

```jldoctest
julia> hasmethod(length, Tuple{Array})
true

julia> f(; oranges=0) = oranges;

julia> hasmethod(f, Tuple{}, (:oranges,))
true

julia> hasmethod(f, Tuple{}, (:apples, :bananas))
false

julia> g(; xs...) = 4;

julia> hasmethod(g, Tuple{}, (:a, :b, :c, :d))  # g 接受任意关键字参数
true
```
