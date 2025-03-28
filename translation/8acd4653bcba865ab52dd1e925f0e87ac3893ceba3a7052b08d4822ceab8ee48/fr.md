```
annotate!(str::AnnotatedString, [range::UnitRange{Int}], label::Symbol, value)
annotate!(str::SubString{AnnotatedString}, [range::UnitRange{Int}], label::Symbol, value)
```

Annoter une `plage` de `str` (ou la chaîne entière) avec une valeur étiquetée (`label` => `value`). Pour supprimer les annotations `label` existantes, utilisez une valeur de `nothing`.

L'ordre dans lequel les annotations sont appliquées à `str` est sémantiquement significatif, comme décrit dans [`AnnotatedString`](@ref).
