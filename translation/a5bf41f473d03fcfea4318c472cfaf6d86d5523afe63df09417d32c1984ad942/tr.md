```
partialsort!(v, k; by=identity, lt=isless, rev=false)
```

Vektörü `v` yerinde kısmen sıralayın, böylece `k` indeksindeki değer (veya `k` bir aralıksa bitişik değerler) tam sıralı olsaydı görüneceği konumda olur. Eğer `k` tek bir indeks ise, o değer döndürülür; eğer `k` bir aralık ise, o indekslerdeki değerlerin bir dizisi döndürülür. `partialsort!`'un girdi dizisini tamamen sıralamayabileceğini unutmayın.

Anahtar kelime argümanları için [`sort!`](@ref) belgesine bakın.

# Örnekler

```jldoctest
julia> a = [1, 2, 4, 3, 4]
5-element Vector{Int64}:
 1
 2
 4
 3
 4

julia> partialsort!(a, 4)
4

julia> a
5-element Vector{Int64}:
 1
 2
 3
 4
 4

julia> a = [1, 2, 4, 3, 4]
5-element Vector{Int64}:
 1
 2
 4
 3
 4

julia> partialsort!(a, 4, rev=true)
2

julia> a
5-element Vector{Int64}:
 4
 4
 3
 2
 1
```
