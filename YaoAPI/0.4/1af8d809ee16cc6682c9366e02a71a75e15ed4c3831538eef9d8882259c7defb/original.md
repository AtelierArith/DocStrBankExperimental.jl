```
focus!(register, locs) -> register
focus!(locs...) -> f(register) -> register
```

Set the active qubits to focused locations, usually used to execute a subroutine. If `register` is not provided, returns a lambda that takes a register as input.

### Examples

```jldoctest; setup=:(using Yao)
julia> reg = product_state(bit"01101")
ArrayReg{2, ComplexF64, Array...}
    active qubits: 5/5
    nlevel: 2

julia> focus!(reg, (1,3,4))
ArrayReg{2, ComplexF64, Array...}
    active qubits: 3/5
    nlevel: 2

julia> measure(reg; nshots=3)
3-element Vector{DitStr{2, 3, Int64}}:
 111 ₍₂₎
 111 ₍₂₎
 111 ₍₂₎

julia> measure(apply(reg, put(3, 2=>X)); nshots=3)
3-element Vector{DitStr{2, 3, Int64}}:
 101 ₍₂₎
 101 ₍₂₎
 101 ₍₂₎
```

Here, we prepare a product state and only look at the qubits 1, 3 and 4. The measurement results are all ones. With the focued register, we can apply a block of size 3 on it, even though the number of qubits is 5.
