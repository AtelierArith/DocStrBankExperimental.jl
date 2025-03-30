```
permute!(v, p)
```

Vektörü `v` yerinde, permütasyon `p`'ye göre permüte et. `p`'nin bir permütasyon olduğunu doğrulamak için herhangi bir kontrol yapılmaz.

Yeni bir permütasyon döndürmek için `v[p]` kullanın. Bu genellikle `permute!(v, p)`'den daha hızlıdır; önceden tahsis edilmiş bir çıktı dizisine `u .= @view v[p]` ile yazmak daha da hızlıdır. (`permute!` yerinde `v`'yi üst üste yazsa da, içsel olarak hangi elemanların taşındığını takip etmek için bazı tahsisatlar gerektirir.)

!!! uyarı     Herhangi bir değiştirilmiş argümanın başka bir argümanla bellek paylaşması durumunda davranış beklenmedik olabilir.

Ayrıca [`invpermute!`](@ref) bakın.

# Örnekler

```jldoctest
julia> A = [1, 1, 3, 4];

julia> perm = [2, 4, 3, 1];

julia> permute!(A, perm);

julia> A
4-element Vector{Int64}:
 1
 4
 3
 1
```
