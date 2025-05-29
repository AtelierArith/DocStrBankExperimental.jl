```
purify(r::DensityMatrix; nbit_env::Int=nactive(r)) -> ArrayReg
```

Get a purification of target density matrix.

### Examples

The following example shows how to measure a local operator on the register, reduced density matrix and the purified register. Their results should be consistent.

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
