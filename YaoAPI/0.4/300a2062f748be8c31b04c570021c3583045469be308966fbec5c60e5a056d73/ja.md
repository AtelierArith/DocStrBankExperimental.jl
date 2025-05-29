```
focus(f, register, locs)
```

呼び出し可能な `f` を `focus` のコンテキストで呼び出します。詳細は [`focus!`](@ref) を参照してください。

### 例

フォーカスされたレジスタを印刷するには

```jldoctest; setup=:(using Yao)
julia> r = arrayreg(bit"101100")
ArrayReg{2, ComplexF64, Array...}
    active qubits: 6/6
    nlevel: 2

julia> focus(x->(println(x);x), r, (1, 2));
ArrayReg{2, ComplexF64, Array...}
    active qubits: 2/6
    nlevel: 2
```
