```
opnorm(A::Adjoint{<:Any,<:AbstractVector}, q::Real=2)
opnorm(A::Transpose{<:Any,<:AbstractVector}, q::Real=2)
```

Für Adjoint/Transpose-umwickelte Vektoren gibt die Funktion die Operator-$q$-Norm von `A` zurück, die äquivalent zur `p`-Norm mit dem Wert `p = q/(q-1)` ist. Sie stimmen bei `p = q = 2` überein. Verwenden Sie [`norm`](@ref), um die `p`-Norm von `A` als Vektor zu berechnen.

Der Unterschied in der Norm zwischen einem Vektorraum und seinem Dualraum entsteht, um die Beziehung zwischen Dualität und dem Skalarprodukt zu bewahren, und das Ergebnis ist konsistent mit der Operator `p`-Norm einer `1 × n`-Matrix.

# Beispiele

```jldoctest
julia> v = [1; im];

julia> vc = v';

julia> opnorm(vc, 1)
1.0

julia> norm(vc, 1)
2.0

julia> norm(v, 1)
2.0

julia> opnorm(vc, 2)
1.4142135623730951

julia> norm(vc, 2)
1.4142135623730951

julia> norm(v, 2)
1.4142135623730951

julia> opnorm(vc, Inf)
2.0

julia> norm(vc, Inf)
1.0

julia> norm(v, Inf)
1.0
```
