```
ComposedFunction{Outer,Inner} <: Function
```

Representa la composición de dos objetos llamables `outer::Outer` y `inner::Inner`. Es decir

```julia
ComposedFunction(outer, inner)(args...; kw...) === outer(inner(args...; kw...))
```

La forma preferida de construir una instancia de `ComposedFunction` es usar el operador de composición [`∘`](@ref):

```jldoctest
julia> sin ∘ cos === ComposedFunction(sin, cos)
true

julia> typeof(sin∘cos)
ComposedFunction{typeof(sin), typeof(cos)}
```

Las piezas compuestas se almacenan en los campos de `ComposedFunction` y se pueden recuperar de la siguiente manera:

```jldoctest
julia> composition = sin ∘ cos
sin ∘ cos

julia> composition.outer === sin
true

julia> composition.inner === cos
true
```

!!! compat "Julia 1.6"
    ComposedFunction requiere al menos Julia 1.6. En versiones anteriores `∘` devuelve una función anónima en su lugar.


Ver también [`∘`](@ref).
