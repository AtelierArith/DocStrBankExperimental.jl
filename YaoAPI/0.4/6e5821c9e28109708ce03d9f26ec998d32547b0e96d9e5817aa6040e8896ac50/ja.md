```
apply!(register, block)
```

量子レジスタに量子回路のブロックを適用します。

!!! note
    新しいブロックのために `apply!` をオーバーロードするには、同じインターフェースを持つ [`unsafe_apply!`](@ref) 関数をオーバーロードしてください。そうすれば、`apply!` インターフェースが入力のサイズチェックを自動的に行います。


### 例

```jldoctest; setup=:(using Yao)
julia> r = zero_state(2)
ArrayReg{2, ComplexF64, Array...}
    active qubits: 2/2
    nlevel: 2

julia> apply!(r, put(2, 1=>X))
ArrayReg{2, ComplexF64, Array...}
    active qubits: 2/2
    nlevel: 2

julia> measure(r;nshots=10)
10-element Vector{DitStr{2, 2, Int64}}:
 01 ₍₂₎
 01 ₍₂₎
 01 ₍₂₎
 01 ₍₂₎
 01 ₍₂₎
 01 ₍₂₎
 01 ₍₂₎
 01 ₍₂₎
 01 ₍₂₎
 01 ₍₂₎
```
