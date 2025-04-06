```
digits([T<:Integer], n::Integer; base::T = 10, pad::Integer = 1)
```

Devuelve un array con tipo de elemento `T` (por defecto `Int`) de los dígitos de `n` en la base dada, opcionalmente rellenado con ceros hasta un tamaño especificado. Los dígitos más significativos están en índices más altos, de modo que `n == sum(digits[k]*base^(k-1) for k in eachindex(digits))`.

Véase también [`ndigits`](@ref), [`digits!`](@ref), y para la base 2 también [`bitstring`](@ref), [`count_ones`](@ref).

# Ejemplos

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
