```
allequal(itr) -> Bool
allequal(f, itr) -> Bool
```

Gibt `true` zurück, wenn alle Werte aus `itr` gleich sind, wenn sie mit [`isequal`](@ref) verglichen werden. Oder wenn alle von `[f(x) for x in itr]` gleich sind, für die zweite Methode.

Beachten Sie, dass `allequal(f, itr)` `f` weniger als `length(itr)`-mal aufrufen kann. Die genaue Anzahl der Aufrufe wird als Implementierungsdetail betrachtet.

Siehe auch: [`unique`](@ref), [`allunique`](@ref).

!!! compat "Julia 1.8"
    Die Funktion `allequal` erfordert mindestens Julia 1.8.


!!! compat "Julia 1.11"
    Die Methode `allequal(f, itr)` erfordert mindestens Julia 1.11.


# Beispiele

```jldoctest
julia> allequal([])
true

julia> allequal([1])
true

julia> allequal([1, 1])
true

julia> allequal([1, 2])
false

julia> allequal(Dict(:a => 1, :b => 1))
false

julia> allequal(abs2, [1, -1])
true
```
