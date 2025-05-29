```
clone(register, n)
```

元の `register` をバッチ次元で `n` 回クローンして [`ArrayReg`](@ref) を作成します。この関数はエミュレーション専用です。

# 例

```jldoctest; setup=:(using YaoArrayRegister)
julia> clone(arrayreg(bit"101"; nbatch=3), 4)
BatchedArrayReg{2, ComplexF64, Array...}
    active qubits: 3/3
    nlevel: 2
    nbatch: 12
```
