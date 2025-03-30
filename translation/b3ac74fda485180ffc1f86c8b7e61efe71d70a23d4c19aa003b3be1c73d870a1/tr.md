```
vec(a::AbstractArray) -> AbstractVector
```

Diziyi `a`'yı bir boyutlu bir sütun vektörü olarak yeniden şekillendirir. Eğer `a` zaten bir `AbstractVector` ise `a`'yı döndürür. Elde edilen dizi, `a` ile aynı temel veriyi paylaşır, bu nedenle yalnızca `a` değiştirilebilir ise değiştirilebilir olacaktır; bu durumda birini değiştirmek diğerini de değiştirecektir.

# Örnekler

```jldoctest
julia> a = [1 2 3; 4 5 6]
2×3 Matrix{Int64}:
 1  2  3
 4  5  6

julia> vec(a)
6-element Vector{Int64}:
 1
 4
 2
 5
 3
 6

julia> vec(1:3)
1:3
```

Ayrıca [`reshape`](@ref), [`dropdims`](@ref) bakınız.
