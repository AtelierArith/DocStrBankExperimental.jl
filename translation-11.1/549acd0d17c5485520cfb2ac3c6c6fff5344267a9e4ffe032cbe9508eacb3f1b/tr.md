```
adjoint!(dest,src)
```

Karmaşık transpoze dizisi `src`'yi alır ve sonucu önceden tahsis edilmiş `dest` dizisine kaydeder; bu dizinin boyutu `(size(src,2),size(src,1))` ile uyumlu olmalıdır. Yerinde transpozisyon desteklenmez ve `src` ile `dest`'in örtüşen bellek bölgeleri varsa beklenmedik sonuçlar ortaya çıkabilir.

# Örnekler

```jldoctest
julia> A = [3+2im 9+2im; 8+7im  4+6im]
2×2 Matrix{Complex{Int64}}:
 3+2im  9+2im
 8+7im  4+6im

julia> B = zeros(Complex{Int64}, 2, 2)
2×2 Matrix{Complex{Int64}}:
 0+0im  0+0im
 0+0im  0+0im

julia> adjoint!(B, A);

julia> B
2×2 Matrix{Complex{Int64}}:
 3-2im  8-7im
 9-2im  4-6im

julia> A
2×2 Matrix{Complex{Int64}}:
 3+2im  9+2im
 8+7im  4+6im
```
