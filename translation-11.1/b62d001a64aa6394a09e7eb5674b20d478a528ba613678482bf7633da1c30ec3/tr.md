```
digits([T<:Integer], n::Integer; base::T = 10, pad::Integer = 1)
```

Verilen tabanda `n`'nin basamaklarını, isteğe bağlı olarak belirtilen boyuta sıfırlarla doldurulmuş `T` (varsayılan `Int`) türünde bir dizi döndürür. Daha anlamlı basamaklar daha yüksek indekslerde yer alır, böylece `n == sum(digits[k]*base^(k-1) for k in eachindex(digits))` olur.

Ayrıca [`ndigits`](@ref), [`digits!`](@ref) ve taban 2 için [`bitstring`](@ref), [`count_ones`](@ref) ile de bakabilirsiniz.

# Örnekler

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
