```
filter(f)
```

`f` fonksiyonunu kullanarak argümanlarını filtreleyen bir fonksiyon oluşturun, yani `x -> filter(f, x)` fonksiyonuna eşdeğer bir fonksiyon.

Dönen fonksiyon `Base.Fix1{typeof(filter)}` türündedir ve özel yöntemler uygulamak için kullanılabilir.

# Örnekler

```jldoctest
julia> (1, 2, Inf, 4, NaN, 6) |> filter(isfinite)
(1, 2, 4, 6)

julia> map(filter(iseven), [1:3, 2:4, 3:5])
3-element Vector{Vector{Int64}}:
 [2]
 [2, 4]
 [4]
```

!!! compat "Julia 1.9"
    Bu yöntem en az Julia 1.9 gerektirir.

