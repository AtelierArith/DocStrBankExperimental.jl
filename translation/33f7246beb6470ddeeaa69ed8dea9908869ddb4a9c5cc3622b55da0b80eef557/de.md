```
parse(type, str; base)
```

Analysiere einen String als eine Zahl. Für `Integer`-Typen kann eine Basis angegeben werden (der Standard ist 10). Für Fließkommatypen wird der String als dezimale Fließkommazahl analysiert. `Complex`-Typen werden aus dezimalen Strings der Form `"R±Iim"` als `Complex(R,I)` des angeforderten Typs analysiert; `"i"` oder `"j"` können auch anstelle von `"im"` verwendet werden, und `"R"` oder `"Iim"` sind ebenfalls zulässig. Wenn der String keine gültige Zahl enthält, wird ein Fehler ausgelöst.

!!! compat "Julia 1.1"
    `parse(Bool, str)` erfordert mindestens Julia 1.1.


# Beispiele

```jldoctest
julia> parse(Int, "1234")
1234

julia> parse(Int, "1234", base = 5)
194

julia> parse(Int, "afc", base = 16)
2812

julia> parse(Float64, "1.2e-3")
0.0012

julia> parse(Complex{Float64}, "3.2e-1 + 4.5im")
0.32 + 4.5im
```
