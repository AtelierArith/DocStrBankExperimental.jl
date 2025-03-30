```
eigen(A, B; sortby) -> GenelleşmişEigen
```

`A` ve `B` matrislerinin genelleşmiş özdeğer ayrıştırmasını hesaplayarak, `F.values` içinde genelleşmiş özdeğerleri ve `F.vectors` matrisinin sütunlarında genelleşmiş özvektörleri içeren bir [`GenelleşmişEigen`](@ref) faktörizasyon nesnesi `F` döndürür. Bu, `Ax =  λBx` biçiminde bir genelleşmiş özdeğer problemini çözmekle ilgilidir; burada `A, B` matrislerdir, `x` bir özvektördür ve `λ` bir özdeğerdir. (`k`'nci genelleşmiş özvektör, `F.vectors[:, k]` diliminden elde edilebilir.)

Ayrıştırmayı yinelemek, `F.values` ve `F.vectors` bileşenlerini üretir.

Varsayılan olarak, özdeğerler ve vektörler `(real(λ),imag(λ))` sıralamasıyla leksikografik olarak sıralanır. `sortby`'ya farklı bir karşılaştırma fonksiyonu `by(λ)` geçirilebilir veya özdeğerleri rastgele bir sırada bırakmak için `sortby=nothing` geçirebilirsiniz.

# Örnekler

```jldoctest
julia> A = [1 0; 0 -1]
2×2 Matrix{Int64}:
 1   0
 0  -1

julia> B = [0 1; 1 0]
2×2 Matrix{Int64}:
 0  1
 1  0

julia> F = eigen(A, B);

julia> F.values
2-element Vector{ComplexF64}:
 0.0 - 1.0im
 0.0 + 1.0im

julia> F.vectors
2×2 Matrix{ComplexF64}:
  0.0+1.0im   0.0-1.0im
 -1.0+0.0im  -1.0-0.0im

julia> vals, vecs = F; # yineleme ile parçalama

julia> vals == F.values && vecs == F.vectors
true
```
