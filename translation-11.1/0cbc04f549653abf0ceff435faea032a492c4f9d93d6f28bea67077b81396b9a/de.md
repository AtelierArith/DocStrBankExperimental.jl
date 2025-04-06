```
filter(f, a)
```

Gibt eine Kopie der Sammlung `a` zurück, wobei Elemente entfernt werden, für die `f` `false` ist. Die Funktion `f` erhält ein Argument.

!!! compat "Julia 1.4"
    Die Unterstützung für `a` als Tuple erfordert mindestens Julia 1.4.


Siehe auch: [`filter!`](@ref), [`Iterators.filter`](@ref).

# Beispiele

```jldoctest
julia> a = 1:10
1:10

julia> filter(isodd, a)
5-element Vector{Int64}:
 1
 3
 5
 7
 9
```
