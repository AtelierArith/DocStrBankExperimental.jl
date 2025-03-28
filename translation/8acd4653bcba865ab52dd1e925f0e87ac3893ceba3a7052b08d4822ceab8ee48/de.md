```
annotate!(str::AnnotatedString, [range::UnitRange{Int}], label::Symbol, value)
annotate!(str::SubString{AnnotatedString}, [range::UnitRange{Int}], label::Symbol, value)
```

Annotieren Sie einen `Bereich` von `str` (oder den gesamten String) mit einem beschrifteten Wert (`label` => `value`). Um vorhandene `label`-Annotationen zu entfernen, verwenden Sie einen Wert von `nothing`.

Die Reihenfolge, in der Annotationen auf `str` angewendet werden, ist semantisch bedeutungsvoll, wie in [`AnnotatedString`](@ref) beschrieben.
