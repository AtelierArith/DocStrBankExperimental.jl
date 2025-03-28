```
allunique(itr) -> Bool
allunique(f, itr) -> Bool
```

Gibt `true` zurück, wenn alle Werte aus `itr` unterschiedlich sind, wenn sie mit [`isequal`](@ref) verglichen werden. Oder wenn alle von `[f(x) for x in itr]` unterschiedlich sind, für die zweite Methode.

Beachten Sie, dass `allunique(f, itr)` `f` weniger als `length(itr)`-Mal aufrufen kann. Die genaue Anzahl der Aufrufe wird als Implementierungsdetail betrachtet.

`allunique` kann eine spezialisierte Implementierung verwenden, wenn die Eingabe sortiert ist.

Siehe auch: [`unique`](@ref), [`issorted`](@ref), [`allequal`](@ref).

!!! compat "Julia 1.11"
    Die Methode `allunique(f, itr)` erfordert mindestens Julia 1.11.


# Beispiele

```jldoctest
julia> allunique([1, 2, 3])
true

julia> allunique([1, 2, 1, 2])
false

julia> allunique(Real[1, 1.0, 2])
false

julia> allunique([NaN, 2.0, NaN, 4.0])
false

julia> allunique(abs, [1, -1, 2])
false
```
