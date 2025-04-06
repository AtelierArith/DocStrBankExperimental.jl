```
abs(x)
```

Der Betrag von `x`.

Wenn `abs` auf vorzeichenbehaftete Ganzzahlen angewendet wird, kann ein Überlauf auftreten, der zur Rückgabe eines negativen Wertes führt. Dieser Überlauf tritt nur auf, wenn `abs` auf den minimal darstellbaren Wert einer vorzeichenbehafteten Ganzzahl angewendet wird. Das heißt, wenn `x == typemin(typeof(x))`, dann ist `abs(x) == x < 0`, nicht `-x`, wie man erwarten könnte.

Siehe auch: [`abs2`](@ref), [`unsigned`](@ref), [`sign`](@ref).

# Beispiele

```jldoctest
julia> abs(-3)
3

julia> abs(1 + im)
1.4142135623730951

julia> abs.(Int8[-128 -127 -126 0 126 127])  # Überlauf bei typemin(Int8)
1×6 Matrix{Int8}:
 -128  127  126  0  126  127

julia> maximum(abs, [1, -2, 3, -4])
4
```
