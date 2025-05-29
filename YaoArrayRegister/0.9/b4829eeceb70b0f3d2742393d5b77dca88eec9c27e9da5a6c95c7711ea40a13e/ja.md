```
ghz_state([T=ComplexF64], n::Int; nbatch::Int=NoBatch())
```

GHZ状態（またはキャット状態）を作成します。これは次のように定義されます。

$$
\frac{|0\rangle^{\otimes n} + |1\rangle^{\otimes n}}{\sqrt{2}}.
$$

### 例

```jldoctest; setup=:(using Yao)
julia> ghz_state(4)
ArrayReg{2, ComplexF64, Array...}
    active qubits: 4/4
    nlevel: 2
```
