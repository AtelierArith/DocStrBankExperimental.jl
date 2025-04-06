```
DateTime(dt::AbstractString, df::DateFormat=ISODateTimeFormat) -> DateTime
```

Construit un `DateTime` en analysant la chaîne de date et d'heure `dt` selon le modèle donné dans l'objet [`DateFormat`](@ref), ou dateformat"yyyy-mm-dd\THH:MM:SS.s" si omis.

Semblable à `DateTime(::AbstractString, ::AbstractString)` mais plus efficace lors de l'analyse répétée de chaînes de date et d'heure au format similaire avec un objet `DateFormat` pré-créé.
