```
!f::Function
```

Negación de función de predicado: cuando el argumento de `!` es una función, devuelve una función compuesta que calcula la negación booleana de `f`.

Véase también [`∘`](@ref).

# Ejemplos

```jldoctest
julia> str = "∀ ε > 0, ∃ δ > 0: |x-y| < δ ⇒ |f(x)-f(y)| < ε"
"∀ ε > 0, ∃ δ > 0: |x-y| < δ ⇒ |f(x)-f(y)| < ε"

julia> filter(isletter, str)
"εδxyδfxfyε"

julia> filter(!isletter, str)
"∀  > 0, ∃  > 0: |-| <  ⇒ |()-()| < "
```

!!! compat "Julia 1.9"
    A partir de Julia 1.9, `!f` devuelve un [`ComposedFunction`](@ref) en lugar de una función anónima.

