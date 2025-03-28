```
@nexprs N expr
```

Generiere `N` Ausdrücke. `expr` sollte ein Ausdruck einer anonymen Funktion sein.

# Beispiele

```jldoctest
julia> @macroexpand Base.Cartesian.@nexprs 4 i -> y[i] = A[i+j]
quote
    y[1] = A[1 + j]
    y[2] = A[2 + j]
    y[3] = A[3 + j]
    y[4] = A[4 + j]
end
```
