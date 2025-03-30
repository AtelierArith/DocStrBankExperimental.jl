```
invpermute!(v, p)
```

[`permute!`](@ref) gibi, ancak verilen permütasyonun tersini uygular.

Eğer önceden tahsis edilmiş bir çıktı diziniz varsa (örneğin `u = similar(v)`), `u[p] = v` kullanmak daha hızlıdır. (`invpermute!` verilerin bir kopyasını dahili olarak tahsis eder.)

!!! uyarı     Herhangi bir değiştirilmiş argümanın, başka bir argümanla bellek paylaşması durumunda davranış beklenmedik olabilir.

# Örnekler

```jldoctest
julia> A = [1, 1, 3, 4];

julia> perm = [2, 4, 3, 1];

julia> invpermute!(A, perm);

julia> A
4-element Vector{Int64}:
 4
 1
 3
 1
```
