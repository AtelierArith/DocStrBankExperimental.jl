```
expect(op::AbstractBlock, reg) -> Vector
expect(op::AbstractBlock, reg => circuit) -> Vector
expect(op::AbstractBlock, density_matrix) -> Vector
```

Get the expectation value of an operator, the second parameter can be a register `reg` or a pair of input register and circuit `reg => circuit`.

```
expect'(op::AbstractBlock, reg=>circuit) -> Pair
expect'(op::AbstractBlock, reg) -> AbstracRegister
```

Obtain the gradient with respect to registers and circuit parameters. For pair input, the second return value is a pair of `gψ=>gparams`, with `gψ` the gradient of input state and `gparams` the gradients of circuit parameters. For register input, the return value is a register.

!!! note
    For batched register, `expect(op, reg=>circuit)` returns a vector of size number of batch as output. However, one can not differentiate over a vector loss, so `expect'(op, reg=>circuit)` accumulates the gradient over batch, rather than returning a batched gradient of parameters.


### Examples

```jldoctest; setup=:(using Yao)
julia> r = normalize!(product_state(bit"11") + product_state(bit"00"))
ArrayReg{2, ComplexF64, Array...}
    active qubits: 2/2
    nlevel: 2

julia> op = chain(2, put(1=>H), put(2=>X))
nqubits: 2
chain
├─ put on (1)
│  └─ H
└─ put on (2)
   └─ X


julia> expect(op, r)
0.7071067811865474
```
