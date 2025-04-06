```
Date(d::AbstractString, df::DateFormat=ISODateFormat) -> Date
```

Construit un `Date` en analysant la chaîne de date `d` suivant le modèle donné dans l'objet [`DateFormat`](@ref), ou dateformat"yyyy-mm-dd" si omis.

Semblable à `Date(::AbstractString, ::AbstractString)` mais plus efficace lors de l'analyse répétée de chaînes de date au format similaire avec un objet `DateFormat` pré-créé.
