```
digits([T<:Integer], n::Integer; base::T = 10, pad::Integer = 1)
```

Gibt ein Array mit dem Elementtyp `T` (Standard `Int`) der Ziffern von `n` in der angegebenen Basis zurück, optional mit Nullen auf eine bestimmte Größe aufgefüllt. Die bedeutenderen Ziffern befinden sich an höheren Indizes, sodass `n == sum(digits[k]*base^(k-1) for k in eachindex(digits))`.

Siehe auch [`ndigits`](@ref), [`digits!`](@ref) und für Basis 2 auch [`bitstring`](@ref), [`count_ones`](@ref).

# Beispiele

```jldoctest
julia> digits(10)
2-element Vector{Int64}:
 0
 1

julia> digits(10, base = 2)
4-element Vector{Int64}:
 0
 1
 0
 1

julia> digits(-256, base = 10, pad = 5)
5-element Vector{Int64}:
 -6
 -5
 -2
  0
  0

julia> n = rand(-999:999);

julia> n == evalpoly(13, digits(n, base = 13))
true
```
