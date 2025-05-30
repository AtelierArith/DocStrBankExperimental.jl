```
DensityMatrix{D,T,MT<:AbstractMatrix{T}} <: AbstractRegister{D}
DensityMatrix{D}(state::AbstractMatrix)
DensityMatrix(state::AbstractMatrix; nlevel=2)
```

密度行列型で、`state`は行列です。型パラメータ`D`はレベルの数で、キーワード引数`nlevel`で指定することもできます。
