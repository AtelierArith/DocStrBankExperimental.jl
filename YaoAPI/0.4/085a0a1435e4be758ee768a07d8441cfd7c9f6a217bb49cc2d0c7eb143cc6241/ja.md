```
append_qudits!(register, n::Int) -> register
append_qudits!(n::Int) -> λ(register)
```

与えられたレジスタに状態 |0> の `n` 個のクディットを追加します。すなわち、|psi> -> |000> ⊗ |psi> となり、追加されたビットは高いインデックスを持ちます。

整数のみが提供された場合、ラムダ関数を返します。

### 例

```jldoctest; setup=:(using Yao)
julia> reg = product_state(bit"01101")
ArrayReg{2, ComplexF64, Array...}
    active qubits: 5/5
    nlevel: 2

julia> append_qudits!(reg, 2)
ArrayReg{2, ComplexF64, Array...}
    active qubits: 7/7
    nlevel: 2

julia> measure(reg; nshots=3)
3-element Vector{DitStr{2, 7, Int64}}:
 0001101 ₍₂₎
 0001101 ₍₂₎
 0001101 ₍₂₎
```

ここで、ビット列は右から左に読み取ります。
