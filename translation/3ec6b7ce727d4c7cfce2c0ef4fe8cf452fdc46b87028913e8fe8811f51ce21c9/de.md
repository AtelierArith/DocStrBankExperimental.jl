```
mergewith!(combine, d::AbstractDict, others::AbstractDict...) -> d
mergewith!(combine)
merge!(combine, d::AbstractDict, others::AbstractDict...) -> d
```

Aktualisieren Sie die Sammlung mit Paaren aus den anderen Sammlungen. Werte mit dem gleichen Schlüssel werden mit der Kombinationsfunktion kombiniert. Die curried Form `mergewith!(combine)` gibt die Funktion `(args...) -> mergewith!(combine, args...)` zurück.

Die Methode `merge!(combine::Union{Function,Type}, args...)` als Alias von `mergewith!(combine, args...)` ist weiterhin aus Gründen der Abwärtskompatibilität verfügbar.

!!! compat "Julia 1.5"
    `mergewith!` erfordert Julia 1.5 oder höher.


# Beispiele

```jldoctest
julia> d1 = Dict(1 => 2, 3 => 4);

julia> d2 = Dict(1 => 4, 4 => 5);

julia> mergewith!(+, d1, d2);

julia> d1
Dict{Int64, Int64} mit 3 Einträgen:
  4 => 5
  3 => 4
  1 => 6

julia> mergewith!(-, d1, d1);

julia> d1
Dict{Int64, Int64} mit 3 Einträgen:
  4 => 0
  3 => 0
  1 => 0

julia> foldl(mergewith!(+), [d1, d2]; init=Dict{Int64, Int64}())
Dict{Int64, Int64} mit 3 Einträgen:
  4 => 5
  3 => 0
  1 => 4
```
