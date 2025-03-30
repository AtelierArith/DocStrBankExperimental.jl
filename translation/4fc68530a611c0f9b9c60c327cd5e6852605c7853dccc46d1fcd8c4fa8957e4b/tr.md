```
dropdims(A; dims)
```

`A` ile aynı verilere sahip bir dizi döndürür, ancak `dims` ile belirtilen boyutlar kaldırılmıştır. `size(A,d)` her `d` için 1 olmalıdır ve tekrar eden boyutlar veya `1:ndims(A)` dışındaki sayılar yasaktır.

Sonuç, `A` ile aynı temel verilere sahiptir; bu nedenle sonuç, yalnızca `A` değiştirilebilir olduğunda değiştirilebilir ve birinin elemanlarını ayarlamak diğerinin değerlerini değiştirir.

Ayrıca bkz: [`reshape`](@ref), [`vec`](@ref).

# Örnekler

```jldoctest
julia> a = reshape(Vector(1:4),(2,2,1,1))
2×2×1×1 Array{Int64, 4}:
[:, :, 1, 1] =
 1  3
 2  4

julia> b = dropdims(a; dims=3)
2×2×1 Array{Int64, 3}:
[:, :, 1] =
 1  3
 2  4

julia> b[1,1,1] = 5; a
2×2×1×1 Array{Int64, 4}:
[:, :, 1, 1] =
 5  3
 2  4
```
