```
zero_state([T=ComplexF64], n::Int; nbatch::Int=NoBatch())
```

状態 $|0\rangle^{\otimes n}$ に初期化された [`AbstractArrayReg`](@ref) を作成します。 [`product_state`](@ref)、[`rand_state`](@ref)、[`uniform_state`](@ref)、および [`ghz_state`](@ref) も参照してください。

### 例

```jldoctest; setup=:(using Yao)
julia> zero_state(4)
ArrayReg{2, ComplexF64, Array...}
    active qubits: 4/4
    nlevel: 2

julia> zero_state(ComplexF32, 4)
ArrayReg{2, ComplexF32, Array...}
    active qubits: 4/4
    nlevel: 2

julia> zero_state(ComplexF32, 4; nbatch=3)
BatchedArrayReg{2, ComplexF32, Transpose...}
    active qubits: 4/4
    nlevel: 2
    nbatch: 3
```
