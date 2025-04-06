```
product(iters...)
```

Birden fazla iteratörün çarpımını döndüren bir iteratör. Üretilen her bir eleman, `i`'nci elemanı `i`'nci argüman iteratöründen gelen bir tuple'dır. İlk iteratör en hızlı değişir.

Ayrıca bkz: [`zip`](@ref), [`Iterators.flatten`](@ref).

# Örnekler

```jldoctest
julia> collect(Iterators.product(1:2, 3:5))
2×3 Matrix{Tuple{Int64, Int64}}:
 (1, 3)  (1, 4)  (1, 5)
 (2, 3)  (2, 4)  (2, 5)

julia> ans == [(x,y) for x in 1:2, y in 3:5]  # Iterators.product içeren bir jeneratörü toplar
true
```
