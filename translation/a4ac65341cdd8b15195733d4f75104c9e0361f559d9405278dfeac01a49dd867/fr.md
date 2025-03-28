```
Some{T}
```

Un type d'enveloppe utilisé dans `Union{Some{T}, Nothing}` pour distinguer l'absence d'une valeur ([`nothing`](@ref)) et la présence d'une valeur `nothing` (c'est-à-dire `Some(nothing)`).

Utilisez [`something`](@ref) pour accéder à la valeur enveloppée par un objet `Some`.
