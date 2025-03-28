```
@printf([io::IO], "%Fmt", args...)
```

Drucke `args` mit einer C `printf`-Stil Formatierungsspezifikationszeichenfolge. Optional kann ein `IO` als erstes Argument übergeben werden, um die Ausgabe umzuleiten.

# Beispiele

```jldoctest
julia> @printf "Hallo %s" "Welt"
Hallo Welt

julia> @printf "Wissenschaftliche Notation %e" 1.234
Wissenschaftliche Notation 1.234000e+00

julia> @printf "Wissenschaftliche Notation drei Stellen %.3e" 1.23456
Wissenschaftliche Notation drei Stellen 1.235e+00

julia> @printf "Dezimal zwei Stellen %.2f" 1.23456
Dezimal zwei Stellen 1.23

julia> @printf "Auf Länge 5 aufgepolstert %5i" 123
Auf Länge 5 aufgepolstert   123

julia> @printf "Mit Nullen auf Länge 6 aufgepolstert %06i" 123
Mit Nullen auf Länge 6 000123

julia> @printf "Verwende kürzere von Dezimal oder wissenschaftlich %g %g" 1.23 12300000.0
Verwende kürzere von Dezimal oder wissenschaftlich 1.23 1.23e+07

julia> @printf "Verwende dynamische Breite und Präzision  %*.*f" 10 2 0.12345
Verwende dynamische Breite und Präzision        0.12
```

Für eine systematische Spezifikation des Formats siehe [hier](https://en.cppreference.com/w/c/io/fprintf). Siehe auch [`@sprintf`](@ref), um das Ergebnis als `String` zu erhalten, anstatt dass es gedruckt wird.

# Hinweise

`Inf` und `NaN` werden konsistent als `Inf` und `NaN` für die Flags `%a`, `%A`, `%e`, `%E`, `%f`, `%F`, `%g` und `%G` gedruckt. Darüber hinaus, wenn eine Fließkommazahl gleich nah an den numerischen Werten von zwei möglichen Ausgabestrings ist, wird der Ausgabestring gewählt, der weiter von null entfernt ist.

# Beispiele

```jldoctest
julia> @printf("%f %F %f %F", Inf, Inf, NaN, NaN)
Inf Inf NaN NaN

julia> @printf "%.0f %.1f %f" 0.5 0.025 -0.0078125
0 0.0 -0.007812
```

!!! compat "Julia 1.8"
    Ab Julia 1.8 werden die Breiten von `%s` (String) und `%c` (Zeichen) unter Verwendung von [`textwidth`](@ref) berechnet, das z.B. Zeichen mit null Breite (wie kombinierende Zeichen für diakritische Zeichen) ignoriert und bestimmte "breite" Zeichen (z.B. Emojis) als Breite `2` behandelt.


!!! compat "Julia 1.10"
    Dynamische Breiten-Spezifizierer wie `%*s` und `%0*.*f` erfordern Julia 1.10.

