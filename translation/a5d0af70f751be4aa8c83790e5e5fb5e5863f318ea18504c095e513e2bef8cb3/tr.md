```
nullspace(M; atol::Real=0, rtol::Real=atol>0 ? 0 : n*ϵ)
nullspace(M, rtol::Real) = nullspace(M; rtol=rtol) # Julia 2.0'da kullanılmayacak

`M`'nin nullspace'inin bir tabanını, `M`'nin en büyük singular değeri `σ₁` için `max(atol, rtol*σ₁)` değerinden daha küçük büyüklüğe sahip singular vektörlerini dahil ederek hesaplar.

Varsayılan olarak, göreceli tolerans `rtol`, `M`'nin en küçük boyutunun büyüklüğü `n` ve `M`'nin eleman tipinin [`eps`](@ref) ile `ϵ`'dir.

# Örnekler

```

jldoctest julia> M = [1 0 0; 0 1 0; 0 0 0] 3×3 Matrix{Int64}:  1  0  0  0  1  0  0  0  0

julia> nullspace(M) 3×1 Matrix{Float64}:  0.0  0.0  1.0

julia> nullspace(M, rtol=3) 3×3 Matrix{Float64}:  0.0  1.0  0.0  1.0  0.0  0.0  0.0  0.0  1.0

julia> nullspace(M, atol=0.95) 3×1 Matrix{Float64}:  0.0  0.0  1.0 ```
