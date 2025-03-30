```
mod1(x, y)
```

Zemin bölme sonrası modül, `mod(r, y) == mod(x, y)` olacak şekilde bir değer `r` döndürür; pozitif `y` için $(0, y]$ aralığında ve negatif `y` için $[y,0)$ aralığında.

Tam sayı argümanları ve pozitif `y` ile bu, `mod(x, 1:y)` ile eşdeğerdir ve bu nedenle 1 tabanlı indeksleme için doğaldır. Karşılaştırıldığında, `mod(x, y) == mod(x, 0:y-1)` ofsetler veya adımlar ile hesaplamalar için doğaldır.

Ayrıca bkz. [`mod`](@ref), [`fld1`](@ref), [`fldmod1`](@ref).

# Örnekler

```jldoctest
julia> mod1(4, 2)
2

julia> mod1.(-5:5, 3)'
1×11 adjoint(::Vector{Int64}) with eltype Int64:
 1  2  3  1  2  3  1  2  3  1  2

julia> mod1.([-0.1, 0, 0.1, 1, 2, 2.9, 3, 3.1]', 3)
1×8 Matrix{Float64}:
 2.9  3.0  0.1  1.0  2.0  2.9  3.0  0.1
```
