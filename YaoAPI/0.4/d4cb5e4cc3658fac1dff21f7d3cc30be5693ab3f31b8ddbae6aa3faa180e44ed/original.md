```
measure([, operator], register[, locs]; nshots=1, rng=Random.GLOBAL_RNG) -> Vector{Int}
```

Measure a quantum state and return measurement results of qudits. This measurement function a cheating version of `measure!` that does not collapse the input state. It also does not need to recompute the quantum state for performing multiple shots measurement.

### Arguments

  * `operator::AbstractBlock` is the operator to measure.
  * `register::AbstractRegister` is the quantum state.
  * `locs` is the qubits to performance the measurement. If `locs` is not provided, all current active qudits are measured (regarding to active qudits,

see [`focus!`](@ref) and [`relax!`](@ref)).

### Keyword arguments

  * `nshots::Int` is the number of shots.
  * `rng` is the random number generator.

### Examples

```jldoctest; setup=:(using Yao)
julia> reg = product_state(bit"110")
ArrayReg{2, ComplexF64, Array...}
    active qubits: 3/3
    nlevel: 2

julia> measure(reg; nshots=3)
3-element Vector{DitStr{2, 3, Int64}}:
 110 ₍₂₎
 110 ₍₂₎
 110 ₍₂₎

julia> measure(reg, (2,3); nshots=3)
3-element Vector{DitStr{2, 2, Int64}}:
 11 ₍₂₎
 11 ₍₂₎
 11 ₍₂₎
```

The following example switches to the X basis for measurement.

```jldoctest; setup=:(using Yao)
julia> reg = apply!(product_state(bit"100"), repeat(3, H, 1:3))
ArrayReg{2, ComplexF64, Array...}
    active qubits: 3/3
    nlevel: 2

julia> measure(repeat(3, X, 1:3), reg; nshots=3)
3-element Vector{ComplexF64}:
 -1.0 + 0.0im
 -1.0 + 0.0im
 -1.0 + 0.0im

julia> reg = apply!(product_state(bit"101"), repeat(3, H, 1:3))
ArrayReg{2, ComplexF64, Array...}
    active qubits: 3/3
    nlevel: 2

julia> measure(repeat(3, X, 1:3), reg; nshots=3)
3-element Vector{ComplexF64}:
 1.0 - 0.0im
 1.0 - 0.0im
 1.0 - 0.0im
```
