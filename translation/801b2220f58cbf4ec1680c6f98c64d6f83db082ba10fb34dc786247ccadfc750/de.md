```
rationalize([T<:Integer=Int,] x; tol::Real=eps(x))
```

Näherungsweise Gleitkommazahl `x` als eine [`Rational`](@ref) Zahl mit Komponenten des angegebenen Ganzzahltyps. Das Ergebnis unterscheidet sich von `x` um nicht mehr als `tol`.

# Beispiele

```jldoctest
julia> rationalize(5.6)
28//5

julia> a = rationalize(BigInt, 10.3)
103//10

julia> typeof(numerator(a))
BigInt
```
