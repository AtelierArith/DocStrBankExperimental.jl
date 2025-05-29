```
DensityMatrix{D,T,MT<:AbstractMatrix{T}} <: AbstractRegister{D}
DensityMatrix{D}(state::AbstractMatrix)
DensityMatrix(state::AbstractMatrix; nlevel=2)
```

Density matrix type, where `state` is a matrix. Type parameter `D` is the number of levels, it can also be specified by a keyword argument `nlevel`.
