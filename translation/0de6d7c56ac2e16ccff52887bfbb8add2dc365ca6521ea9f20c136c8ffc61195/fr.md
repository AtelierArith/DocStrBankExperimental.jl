```
!f::Function
```

Négation de fonction prédicat : lorsque l'argument de `!` est une fonction, cela renvoie une fonction composée qui calcule la négation booléenne de `f`.

Voir aussi [`∘`](@ref).

# Exemples

```jldoctest
julia> str = "∀ ε > 0, ∃ δ > 0: |x-y| < δ ⇒ |f(x)-f(y)| < ε"
"∀ ε > 0, ∃ δ > 0: |x-y| < δ ⇒ |f(x)-f(y)| < ε"

julia> filter(isletter, str)
"εδxyδfxfyε"

julia> filter(!isletter, str)
"∀  > 0, ∃  > 0: |-| <  ⇒ |()-()| < "
```

!!! compat "Julia 1.9"
    À partir de Julia 1.9, `!f` renvoie une [`ComposedFunction`](@ref) au lieu d'une fonction anonyme.

