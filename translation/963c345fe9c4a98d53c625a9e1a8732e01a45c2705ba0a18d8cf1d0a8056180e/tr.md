```
length(A::AbstractArray)
```

Dizinin içindeki eleman sayısını döndürür, varsayılan olarak `prod(size(A))` kullanılır.

# Örnekler

```jldoctest
julia> length([1, 2, 3, 4])
4

julia> length([1 2; 3 4])
4
```
