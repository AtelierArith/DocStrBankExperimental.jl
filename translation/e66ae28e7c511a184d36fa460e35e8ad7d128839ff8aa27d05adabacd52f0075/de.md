```
ComposedFunction{Outer,Inner} <: Funktion
```

Stellt die Komposition von zwei aufrufbaren Objekten `outer::Outer` und `inner::Inner` dar. Das heißt

```julia
ComposedFunction(outer, inner)(args...; kw...) === outer(inner(args...; kw...))
```

Die bevorzugte Methode zur Konstruktion einer Instanz von `ComposedFunction` ist die Verwendung des Kompositionsoperators [`∘`](@ref):

```jldoctest
julia> sin ∘ cos === ComposedFunction(sin, cos)
true

julia> typeof(sin∘cos)
ComposedFunction{typeof(sin), typeof(cos)}
```

Die zusammengesetzten Teile werden in den Feldern von `ComposedFunction` gespeichert und können wie folgt abgerufen werden:

```jldoctest
julia> composition = sin ∘ cos
sin ∘ cos

julia> composition.outer === sin
true

julia> composition.inner === cos
true
```

!!! compat "Julia 1.6"
    ComposedFunction erfordert mindestens Julia 1.6. In früheren Versionen gibt `∘` eine anonyme Funktion zurück.


Siehe auch [`∘`](@ref).
