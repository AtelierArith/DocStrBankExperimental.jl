```
@big_str str
```

Analysiere einen String in eine [`BigInt`](@ref) oder [`BigFloat`](@ref) und werfe einen `ArgumentError`, wenn der String keine gültige Zahl ist. Für ganze Zahlen ist `_` im String als Trennzeichen erlaubt.

# Beispiele

```jldoctest
julia> big"123_456"
123456

julia> big"7891.5"
7891.5

julia> big"_"
ERROR: ArgumentError: ungültiges Zahlenformat _ für BigInt oder BigFloat
[...]
```

!!! warning
    Die Verwendung von `@big_str` zur Konstruktion von [`BigFloat`](@ref) Werten kann nicht das Verhalten ergeben, das naiv erwartet werden könnte: Als Makro befolgt `@big_str` die globalen Präzisionseinstellungen ([`setprecision`](@ref)) und Rundungsmodus ([`setrounding`](@ref)) so, wie sie zur *Ladezeit* sind. Daher gibt eine Funktion wie `() -> precision(big"0.3")` eine Konstante zurück, deren Wert von der Präzision zum Zeitpunkt der Definition der Funktion abhängt, **nicht** von der Präzision zum Zeitpunkt des Aufrufs der Funktion.

