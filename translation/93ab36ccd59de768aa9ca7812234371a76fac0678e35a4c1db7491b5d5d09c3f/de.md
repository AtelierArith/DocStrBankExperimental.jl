```
isapprox(x, y; atol::Real=0, rtol::Real=atol>0 ? 0 : √eps, nans::Bool=false[, norm::Function])
```

Ungenaue Gleichheitsvergleiche. Zwei Zahlen vergleichen sich gleich, wenn ihre relative Distanz *oder* ihre absolute Distanz innerhalb der Toleranzgrenzen liegt: `isapprox` gibt `true` zurück, wenn `norm(x-y) <= max(atol, rtol*max(norm(x), norm(y)))`. Der Standardwert für `atol` (absolute Toleranz) ist null und der Standardwert für `rtol` (relative Toleranz) hängt von den Typen von `x` und `y` ab. Das Schlüsselwortargument `nans` bestimmt, ob NaN-Werte als gleich betrachtet werden oder nicht (Standardwert ist false).

Für reale oder komplexe Gleitkommawerte, wenn kein `atol > 0` angegeben ist, ist der Standardwert für `rtol` die Quadratwurzel von [`eps`](@ref) des Typs von `x` oder `y`, je nachdem, welcher größer ist (am wenigsten präzise). Dies entspricht der Anforderung, dass etwa die Hälfte der signifikanten Ziffern gleich sein muss. Andernfalls, z. B. für ganzzahlige Argumente oder wenn ein `atol > 0` angegeben ist, ist der Standardwert für `rtol` null.

Das Schlüsselwort `norm` hat standardmäßig `abs` für numerische `(x,y)` und `LinearAlgebra.norm` für Arrays (wo eine alternative `norm`-Wahl manchmal nützlich ist). Wenn `x` und `y` Arrays sind, fällt der Vergleich zurück auf die Überprüfung, ob alle Elemente von `x` und `y komponentenweise ungefähr gleich sind, wenn`norm(x-y)`nicht endlich ist (d. h.`±Inf`oder`NaN`).

Der binäre Operator `≈` ist äquivalent zu `isapprox` mit den Standardargumenten, und `x ≉ y` ist äquivalent zu `!isapprox(x,y)`.

Beachten Sie, dass `x ≈ 0` (d. h. der Vergleich mit null unter den Standardtoleranzen) äquivalent zu `x == 0` ist, da der Standardwert für `atol` `0` ist. In solchen Fällen sollten Sie entweder eine geeignete `atol` angeben (oder `norm(x) ≤ atol` verwenden) oder Ihren Code umstellen (z. B. `x ≈ y` anstelle von `x - y ≈ 0` verwenden). Es ist nicht möglich, automatisch eine von null verschiedene `atol` auszuwählen, da sie von der gesamten Skalierung (den "Einheiten") Ihres Problems abhängt: Zum Beispiel ist in `x - y ≈ 0` `atol=1e-9` eine absurd kleine Toleranz, wenn `x` der [Radius der Erde](https://en.wikipedia.org/wiki/Earth_radius) in Metern ist, aber eine absurd große Toleranz, wenn `x` der [Radius eines Wasserstoffatoms](https://en.wikipedia.org/wiki/Bohr_radius) in Metern ist.

!!! compat "Julia 1.6"
    Das Übergeben des Schlüsselwortarguments `norm` beim Vergleichen numerischer (nicht-array) Argumente erfordert Julia 1.6 oder höher.


# Beispiele

```jldoctest
julia> isapprox(0.1, 0.15; atol=0.05)
true

julia> isapprox(0.1, 0.15; rtol=0.34)
true

julia> isapprox(0.1, 0.15; rtol=0.33)
false

julia> 0.1 + 1e-10 ≈ 0.1
true

julia> 1e-10 ≈ 0
false

julia> isapprox(1e-10, 0, atol=1e-8)
true

julia> isapprox([10.0^9, 1.0], [10.0^9, 2.0]) # using `norm`
true
```
