```
select!(dest::AbstractRegister, src::AbstractRegister, bits::Integer...) -> AbstractRegister
select!(register::AbstractRegister, bits::Integer...) -> register
select!(b::Integer) -> f(register)
```

入力固有状態 `bits` に基づいて与えられた量子状態のサブスペースを選択します。非インプレースバージョンについては、[`select`](@ref) を参照してください。レジスタが提供されていない場合、レジスタを入力として受け取るラムダ式を返します。

### 例

```jldoctest; setup=:(using Yao)
julia> reg = ghz_state(3)
ArrayReg{2, ComplexF64, Array...}
    active qubits: 3/3
    nlevel: 2

julia> select!(reg, bit"111")
ArrayReg{2, ComplexF64, Array...}
    active qubits: 0/0
    nlevel: 2

julia> norm(reg)
0.7071067811865476
```

選択はアクティブな量子ビットに対してのみ機能します。例えば、

```
julia> reg = focus!(ghz_state(3), (1, 2))
ArrayReg{2, ComplexF64, Array...}
    active qubits: 2/3
    nlevel: 2

julia> select!(reg, bit"11")
ArrayReg{2, ComplexF64, Array...}
    active qubits: 0/1
    nlevel: 2

julia> statevec(reg)
1×2 Matrix{ComplexF64}:
 0.0+0.0im  0.707107+0.0im
```

!!! tip
    開発者は `select!(r::RegisterType, bits::NTuple{N, <:Integer})` をオーバーロードすべきであり、`bits` が特定のビット数（例: `Int64`）を持つと仮定すべきではありません。そうしないと、利用可能な最大のクディット数が制限されます。

