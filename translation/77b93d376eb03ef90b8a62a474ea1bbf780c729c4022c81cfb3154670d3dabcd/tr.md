```
partialsortperm!(ix, v, k; by=identity, lt=isless, rev=false)
```

[`partialsortperm`](@ref) gibi, `v` ile aynı boyutta önceden tahsis edilmiş bir indeks vektörü `ix` kabul eder; bu vektör, `v`'nin indekslerinin (bir permütasyonu) saklanması için kullanılır.

`ix`, `v`'nin indekslerini içerecek şekilde başlatılır.

(Genellikle, `v`'nin indeksleri `1:length(v)` olacaktır, ancak `v`'nin `OffsetArray` gibi bir alternatif dizi türü varsa ve bu tür bir-bir tabanlı indeksler içermiyorsa, `ix` bu aynı indeksleri paylaşmalıdır.)

Dönüşte, `ix`'in, aşağıdaki gibi sıralı konumlarında `k` indekslerini içermesi garanti edilir:

```julia
partialsortperm!(ix, v, k);
v[ix[k]] == partialsort(v, k)
```

Dönüş değeri, `k` bir tam sayı ise `ix`'in `k`'nci elemanıdır, ya da `k` bir aralık ise `ix`'e bir görünüm (view) olacaktır.

!!! uyarı     Herhangi bir değiştirilmiş argümanın, başka bir argümanla bellek paylaşması durumunda davranış beklenmedik olabilir.

# Örnekler

```jldoctest
julia> v = [3, 1, 2, 1];

julia> ix = Vector{Int}(undef, 4);

julia> partialsortperm!(ix, v, 1)
2

julia> ix = [1:4;];

julia> partialsortperm!(ix, v, 2:3)
2-element view(::Vector{Int64}, 2:3) with eltype Int64:
 4
 3
```

```
