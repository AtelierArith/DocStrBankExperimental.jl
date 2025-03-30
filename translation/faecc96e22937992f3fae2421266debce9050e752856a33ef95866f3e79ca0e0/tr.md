```
resize!(a::Vector, n::Integer) -> Vector
```

`a`'yı `n` eleman içerecek şekilde yeniden boyutlandırır. Eğer `n`, mevcut koleksiyon uzunluğundan küçükse, ilk `n` eleman korunur. Eğer `n` daha büyükse, yeni elemanların başlatılacağı garanti edilmez.

# Örnekler

```jldoctest
julia> resize!([6, 5, 4, 3, 2, 1], 3)
3-element Vector{Int64}:
 6
 5
 4

julia> a = resize!([6, 5, 4, 3, 2, 1], 8);

julia> length(a)
8

julia> a[1:6]
6-element Vector{Int64}:
 6
 5
 4
 3
 2
 1
```
