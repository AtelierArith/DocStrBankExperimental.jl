```
uniform_state([T=ComplexF64], n; nbatch=NoBatch(), no_transpose_storage=false)
```

一様状態を作成します：

$$
\frac{1}{\sqrt{2^n}} \sum_{k=0}^{2^{n}-1} |k\rangle.
$$

この状態は、$|00⋯00⟩$ 状態に `H`（ハダマードゲート）を適用することでも作成できます。

### 例

```jldoctest; setup=:(using Yao)
julia> uniform_state(4; nbatch=2)
BatchedArrayReg{2, ComplexF64, Transpose...}
    active qubits: 4/4
    nlevel: 2
    nbatch: 2

julia> uniform_state(ComplexF32, 4; nbatch=2)
BatchedArrayReg{2, ComplexF32, Transpose...}
    active qubits: 4/4
    nlevel: 2
    nbatch: 2
```
