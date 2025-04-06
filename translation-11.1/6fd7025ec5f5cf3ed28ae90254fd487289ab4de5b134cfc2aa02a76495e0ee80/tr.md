```
foreach(f, c...) -> Hiçbir şey
```

Fonksiyon `f`'yi iterable `c`'nin her bir elemanı üzerinde çağırır. Birden fazla iterable argümanı için, `f` eleman bazında çağrılır ve herhangi bir iterator bittiğinde iterasyon durur.

`foreach`, `f`'nin sonuçlarının gerekli olmadığı durumlarda [`map`](@ref) yerine kullanılmalıdır; örneğin `foreach(println, array)`.

# Örnekler

```jldoctest
julia> tri = 1:3:7; res = Int[];

julia> foreach(x -> push!(res, x^2), tri)

julia> res
3-element Vector{Int64}:
  1
 16
 49

julia> foreach((x, y) -> println(x, " ile ", y), tri, 'a':'z')
1 ile a
4 ile b
7 ile c
```
