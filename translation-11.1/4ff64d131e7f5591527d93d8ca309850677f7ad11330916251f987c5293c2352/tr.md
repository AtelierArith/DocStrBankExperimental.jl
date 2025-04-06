```
ldlt(S::SymTridiagonal) -> LDLt
```

Gerçek simetrik tridiagonal matris `S` için `LDLt` (yani, $LDL^T$) faktorizasyonu hesaplayın; burada `S = L*Diagonal(d)*L'` şeklindedir ve `L` birim alt üçgen matris, `d` ise bir vektördür. `F = ldlt(S)` şeklindeki bir `LDLt` faktorizasyonunun ana kullanımı, `Sx = b` doğrusal denklemler sistemini `F\b` ile çözmektir.

Benzer, ancak pivotlu, genel simetrik veya Hermit matrislerin faktorizasyonu için [`bunchkaufman`](@ref) kısmına da bakın.

# Örnekler

```jldoctest
julia> S = SymTridiagonal([3., 4., 5.], [1., 2.])
3×3 SymTridiagonal{Float64, Vector{Float64}}:
 3.0  1.0   ⋅
 1.0  4.0  2.0
  ⋅   2.0  5.0

julia> ldltS = ldlt(S);

julia> b = [6., 7., 8.];

julia> ldltS \ b
3-element Vector{Float64}:
 1.7906976744186047
 0.627906976744186
 1.3488372093023255

julia> S \ b
3-element Vector{Float64}:
 1.7906976744186047
 0.627906976744186
 1.3488372093023255
```
