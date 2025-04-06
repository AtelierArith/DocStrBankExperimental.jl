```
Time(t::AbstractString, df::DateFormat=ISOTimeFormat) -> Time
```

Construit un `Time` en analysant la chaîne de date et heure `t` suivant le modèle donné dans l'objet [`DateFormat`](@ref), ou dateformat"HH:MM:SS.s" si omis.

Semblable à `Time(::AbstractString, ::AbstractString)` mais plus efficace lors de l'analyse répétée de chaînes de temps au format similaire avec un objet `DateFormat` pré-créé.
