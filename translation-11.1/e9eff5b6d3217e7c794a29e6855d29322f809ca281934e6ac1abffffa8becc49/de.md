```
@nref N A indexexpr
```

Generiere Ausdrücke wie `A[i_1, i_2, ...]`. `indexexpr` kann entweder ein Iterationssymbol-Präfix oder ein anonymer Funktionsausdruck sein.

# Beispiele

```jldoctest
julia> @macroexpand Base.Cartesian.@nref 3 A i
:(A[i_1, i_2, i_3])
```
