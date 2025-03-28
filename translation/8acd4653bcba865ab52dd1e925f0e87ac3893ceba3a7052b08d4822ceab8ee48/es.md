```
annotate!(str::AnnotatedString, [range::UnitRange{Int}], label::Symbol, value)
annotate!(str::SubString{AnnotatedString}, [range::UnitRange{Int}], label::Symbol, value)
```

Anotar un `rango` de `str` (o la cadena completa) con un valor etiquetado (`label` => `value`). Para eliminar anotaciones de `label` existentes, utiliza un valor de `nothing`.

El orden en el que se aplican las anotaciones a `str` es semánticamente significativo, como se describe en [`AnnotatedString`](@ref).
