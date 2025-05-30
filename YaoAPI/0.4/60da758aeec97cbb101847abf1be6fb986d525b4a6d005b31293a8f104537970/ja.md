```
purify(r::DensityMatrix; nbit_env::Int=nactive(r)) -> ArrayReg
```

ターゲット密度行列の浄化を取得します。

### 例

以下の例は、レジスタ、縮退密度行列、および浄化されたレジスタ上でローカルオペレーターを測定する方法を示しています。それらの結果は一貫しているはずです。

```jldoctest; setup=:(using Yao, Random; Random.seed!(123))
julia> reg = ghz_state(3)
ArrayReg{2, ComplexF64, Array...}
    active qubits: 3/3
    nlevel: 2

julia> r = density_matrix(reg, (2,));

julia> preg = purify(r)
ArrayReg{2, ComplexF64, Array...}
    active qubits: 1/2
    nlevel: 2

julia> isapprox(expect(Z + Y, preg), 0.0; atol=1e-10)
true

julia> isapprox(expect(Z + Y, r), 0.0; atol=1e-10)
true

julia> isapprox(expect(put(3, 2=>(Z + Y)), reg), 0.0; atol=1e-10)
true
```
