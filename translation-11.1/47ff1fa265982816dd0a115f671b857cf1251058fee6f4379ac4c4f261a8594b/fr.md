```
digits!(array, n::Integer; base::Integer = 10)
```

Remplit un tableau des chiffres de `n` dans la base donnée. Les chiffres les plus significatifs se trouvent à des indices plus élevés. Si la longueur du tableau est insuffisante, les chiffres les moins significatifs sont remplis jusqu'à la longueur du tableau. Si la longueur du tableau est excessive, la portion excédentaire est remplie de zéros.

# Exemples

```jldoctest
julia> digits!([2, 2, 2, 2], 10, base = 2)
4-element Vector{Int64}:
 0
 1
 0
 1

julia> digits!([2, 2, 2, 2, 2, 2], 10, base = 2)
6-element Vector{Int64}:
 0
 1
 0
 1
 0
 0
```
