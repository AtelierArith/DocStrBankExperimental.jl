```
!f::Function
```

谓词函数否定：当 `!` 的参数是一个函数时，它返回一个组合函数，该函数计算 `f` 的布尔否定。

另见 [`∘`](@ref)。

# 示例

```jldoctest
julia> str = "∀ ε > 0, ∃ δ > 0: |x-y| < δ ⇒ |f(x)-f(y)| < ε"
"∀ ε > 0, ∃ δ > 0: |x-y| < δ ⇒ |f(x)-f(y)| < ε"

julia> filter(isletter, str)
"εδxyδfxfyε"

julia> filter(!isletter, str)
"∀  > 0, ∃  > 0: |-| <  ⇒ |()-()| < "
```

!!! compat "Julia 1.9"
    从 Julia 1.9 开始，`!f` 返回一个 [`ComposedFunction`](@ref) 而不是一个匿名函数。

