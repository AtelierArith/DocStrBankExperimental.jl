```
AbstractDict{K, V}
```

Obertyp für dictionary-ähnliche Typen mit Schlüsseln vom Typ `K` und Werten vom Typ `V`. [`Dict`](@ref), [`IdDict`](@ref) und andere Typen sind Untertypen davon. Ein `AbstractDict{K, V}` sollte ein Iterator von `Pair{K, V}` sein.
