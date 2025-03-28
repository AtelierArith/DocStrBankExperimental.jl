```
*(x, y...)
```

Multiplikationsoperator.

Infix `x*y*z*...` ruft diese Funktion mit allen Argumenten auf, d.h. `*(x, y, z, ...)`, die standardmäßig dann `(x*y) * z * ...` von links aus aufruft.

Juxtaposition wie `2pi` ruft ebenfalls `*(2, pi)` auf. Beachten Sie, dass diese Operation eine höhere Priorität hat als ein literales `*`. Beachten Sie auch, dass die Juxtaposition "0x..." (ganzzahlig null mal eine Variable, deren Name mit `x` beginnt) verboten ist, da sie mit nicht signierten Ganzzahl-Literalen in Konflikt steht: `0x01 isa UInt8`.

Beachten Sie, dass Überlauf für die meisten Ganzzahltypen, einschließlich des Standardtyps `Int`, beim Multiplizieren großer Zahlen möglich ist.

# Beispiele

```jldoctest
julia> 2 * 7 * 8
112

julia> *(2, 7, 8)
112

julia> [2 0; 0 3] * [1, 10]  # Matrix * Vektor
2-element Vector{Int64}:
  2
 30

julia> 1/2pi, 1/2*pi  # Juxtaposition hat höhere Priorität
(0.15915494309189535, 1.5707963267948966)

julia> x = [1, 2]; x'x  # adjungierter Vektor * Vektor
5
```
