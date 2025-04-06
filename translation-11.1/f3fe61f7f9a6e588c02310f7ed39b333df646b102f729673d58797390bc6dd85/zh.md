```
f ∘ g
```

组合函数：即 `(f ∘ g)(args...; kwargs...)` 意味着 `f(g(args...; kwargs...))`。在 Julia REPL（以及大多数适当配置的编辑器）中，可以通过输入 `\circ<tab>` 来输入 `∘` 符号。

函数组合也可以以前缀形式工作：`∘(f, g)` 与 `f ∘ g` 相同。前缀形式支持多个函数的组合：`∘(f, g, h) = f ∘ g ∘ h` 和展开 `∘(fs...)` 用于组合一个可迭代的函数集合。`∘` 的最后一个参数首先执行。

!!! compat "Julia 1.4"
    多重函数组合至少需要 Julia 1.4。


!!! compat "Julia 1.5"
    组合一个函数 ∘(f) 至少需要 Julia 1.5。


!!! compat "Julia 1.7"
    使用关键字参数至少需要 Julia 1.7。


# 示例

```jldoctest
julia> map(uppercase∘first, ["apple", "banana", "carrot"])
3-element Vector{Char}:
 'A': ASCII/Unicode U+0041 (category Lu: Letter, uppercase)
 'B': ASCII/Unicode U+0042 (category Lu: Letter, uppercase)
 'C': ASCII/Unicode U+0043 (category Lu: Letter, uppercase)

julia> (==(6)∘length).(["apple", "banana", "carrot"])
3-element BitVector:
 0
 1
 1

julia> fs = [
           x -> 2x
           x -> x-1
           x -> x/2
           x -> x+1
       ];

julia> ∘(fs...)(3)
2.0
```

另请参见 [`ComposedFunction`](@ref), [`!f::Function`](@ref).
