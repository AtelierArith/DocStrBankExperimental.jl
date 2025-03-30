```
splice!(a::Vector, index::Integer, [replacement]) -> item
```

Verilen indeksteki öğeyi kaldırır ve kaldırılan öğeyi döndürür. Sonraki öğeler, oluşan boşluğu doldurmak için sola kaydırılır. Belirtilirse, sıralı bir koleksiyondan gelen yer tutucu değerler, kaldırılan öğenin yerine yerleştirilecektir.

Ayrıca bakınız: [`replace`](@ref), [`delete!`](@ref), [`deleteat!`](@ref), [`pop!`](@ref), [`popat!`](@ref).

# Örnekler

```jldoctest
julia> A = [6, 5, 4, 3, 2, 1]; splice!(A, 5)
2

julia> A
5-element Vector{Int64}:
 6
 5
 4
 3
 1

julia> splice!(A, 5, -1)
1

julia> A
5-element Vector{Int64}:
  6
  5
  4
  3
 -1

julia> splice!(A, 1, [-1, -2, -3])
6

julia> A
7-element Vector{Int64}:
 -1
 -2
 -3
  5
  4
  3
 -1
```

Herhangi bir öğeyi kaldırmadan `replacement`'ı bir indeks `n`'den önce eklemek için `splice!(collection, n:n-1, replacement)` kullanın.
