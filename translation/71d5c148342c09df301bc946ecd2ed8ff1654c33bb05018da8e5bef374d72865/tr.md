```
unique(f, itr)
```

`itr`'den elde edilen her benzersiz değer için `f` uygulanarak bir değer içeren bir dizi döndürür.

# Örnekler

```jldoctest
julia> unique(x -> x^2, [1, -1, 3, -3, 4])
3-element Vector{Int64}:
 1
 3
 4
```

Bu işlevsellik, bir dizideki benzersiz elemanların ilk oluşumlarının *indekslerini* çıkarmak için de kullanılabilir:

```jldoctest
julia> a = [3.1, 4.2, 5.3, 3.1, 3.1, 3.1, 4.2, 1.7];

julia> i = unique(i -> a[i], eachindex(a))
4-element Vector{Int64}:
 1
 2
 3
 8

julia> a[i]
4-element Vector{Float64}:
 3.1
 4.2
 5.3
 1.7

julia> a[i] == unique(a)
true
```
