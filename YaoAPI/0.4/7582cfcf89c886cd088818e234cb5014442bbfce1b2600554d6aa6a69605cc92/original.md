```
select!(dest::AbstractRegister, src::AbstractRegister, bits::Integer...) -> AbstractRegister
select!(register::AbstractRegister, bits::Integer...) -> register
select!(b::Integer) -> f(register)
```

select a subspace of given quantum state based on input eigen state `bits`. See also [`select`](@ref) for the non-inplace version. If the register is not provided, it returns a lambda expression that takes a register as the input.

### Examples

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

The selection only works on the activated qubits, for example

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
    Developers should overload `select!(r::RegisterType, bits::NTuple{N, <:Integer})` and do not assume `bits` has specific number of bits (e.g `Int64`), or it will restrict the its maximum available number of qudits.

