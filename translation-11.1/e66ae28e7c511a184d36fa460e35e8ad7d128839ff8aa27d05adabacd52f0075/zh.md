```
ComposedFunction{Outer,Inner} <: Function
```

表示两个可调用对象 `outer::Outer` 和 `inner::Inner` 的组合。也就是说

```julia
ComposedFunction(outer, inner)(args...; kw...) === outer(inner(args...; kw...))
```

构造 `ComposedFunction` 实例的首选方式是使用组合运算符 [`∘`](@ref):

```jldoctest
julia> sin ∘ cos === ComposedFunction(sin, cos)
true

julia> typeof(sin∘cos)
ComposedFunction{typeof(sin), typeof(cos)}
```

组合的部分存储在 `ComposedFunction` 的字段中，可以通过以下方式检索：

```jldoctest
julia> composition = sin ∘ cos
sin ∘ cos

julia> composition.outer === sin
true

julia> composition.inner === cos
true
```

!!! compat "Julia 1.6"
    ComposedFunction 至少需要 Julia 1.6。在早期版本中，`∘` 返回一个匿名函数。


另见 [`∘`](@ref).
