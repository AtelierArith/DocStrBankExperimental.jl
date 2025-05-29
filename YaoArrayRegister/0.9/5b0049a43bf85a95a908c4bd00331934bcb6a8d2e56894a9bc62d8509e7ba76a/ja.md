```
arrayreg([T=ComplexF64], bit_str; nbatch=NoBatch())
```

ビット文字列リテラルから配列レジスタを構築します。ビット文字列リテラルについては、[`@bit_str`](@ref)を参照してください。

### 例

```jldoctest; setup=:(using Yao)
julia> arrayreg(bit"1010")
ArrayReg{2, ComplexF64, Array...}
    active qubits: 4/4
    nlevel: 2

julia> arrayreg(ComplexF32, bit"1010")
ArrayReg{2, ComplexF32, Array...}
    active qubits: 4/4
    nlevel: 2
```
