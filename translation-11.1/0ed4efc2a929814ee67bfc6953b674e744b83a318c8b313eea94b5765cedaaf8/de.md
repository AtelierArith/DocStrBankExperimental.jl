```
map!(f, values(dict::AbstractDict))
```

Modifiziert `dict`, indem jeder Wert von `val` in `f(val)` umgewandelt wird. Beachten Sie, dass der Typ von `dict` nicht geändert werden kann: Wenn `f(val)` kein Beispiel des Wertetyps von `dict` ist, wird es, wenn möglich, in den Wertetyp umgewandelt, andernfalls wird ein Fehler ausgelöst.

!!! compat "Julia 1.2"
    `map!(f, values(dict::AbstractDict))` erfordert Julia 1.2 oder höher.


# Beispiele

```jldoctest
julia> d = Dict(:a => 1, :b => 2)
Dict{Symbol, Int64} mit 2 Einträgen:
  :a => 1
  :b => 2

julia> map!(v -> v-1, values(d))
ValueIterator für ein Dict{Symbol, Int64} mit 2 Einträgen. Werte:
  0
  1
```
