```
!f::Funktion
```

Prädikatfunktion Negation: Wenn das Argument von `!` eine Funktion ist, gibt es eine zusammengesetzte Funktion zurück, die die boolesche Negation von `f` berechnet.

Siehe auch [`∘`](@ref).

# Beispiele

```jldoctest
julia> str = "∀ ε > 0, ∃ δ > 0: |x-y| < δ ⇒ |f(x)-f(y)| < ε"
"∀ ε > 0, ∃ δ > 0: |x-y| < δ ⇒ |f(x)-f(y)| < ε"

julia> filter(isletter, str)
"εδxyδfxfyε"

julia> filter(!isletter, str)
"∀  > 0, ∃  > 0: |-| <  ⇒ |()-()| < "
```

!!! compat "Julia 1.9"
    Ab Julia 1.9 gibt `!f` eine [`ComposedFunction`](@ref) zurück, anstatt einer anonymen Funktion.

