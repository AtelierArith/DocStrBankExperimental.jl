```
IdSet{T}([itr])
IdSet()
```

IdSet{T}() konstruiert eine Menge (siehe [`Set`](@ref)), die `===` als Gleichheit mit Werten des Typs `T` verwendet.

Im folgenden Beispiel sind die Werte alle `isequal`, sodass sie in der gewöhnlichen `Set` überschrieben werden. Das `IdSet` vergleicht mit `===` und bewahrt somit die 3 unterschiedlichen Werte.

# Beispiele

```jldoctest; filter = r"\n\s*(1|1\.0|true)"
julia> Set(Any[true, 1, 1.0])
Set{Any} mit 1 Element:
  1.0

julia> IdSet{Any}(Any[true, 1, 1.0])
IdSet{Any} mit 3 Elementen:
  1.0
  1
  true
```
