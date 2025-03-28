```
digits([T<:Integer], n::Integer; base::T = 10, pad::Integer = 1)
```

Renvoie un tableau avec un type d'élément `T` (par défaut `Int`) des chiffres de `n` dans la base donnée, éventuellement complété par des zéros à une taille spécifiée. Les chiffres les plus significatifs se trouvent à des indices plus élevés, de sorte que `n == sum(digits[k]*base^(k-1) for k in eachindex(digits))`.

Voir aussi [`ndigits`](@ref), [`digits!`](@ref), et pour la base 2 également [`bitstring`](@ref), [`count_ones`](@ref).

# Exemples

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
