```
measure!([postprocess,] [operator, ]register[, locs]; rng=Random.GLOBAL_RNG)
```

Measure current active qudits or qudits at `locs`. If the operator is not provided, it will measure on the computational basis and collapse to a product state. Otherwise, the quantum state collapse to the subspace corresponds to the resulting eigenvalue of the observable.

### Arguments

  * `postprocess` is the postprocessing method, it can be

      * `NoPostProcess()` (default).
      * `ResetTo(config)`, reset to result state to `config`. It can not be used if `operator` is provided, because measuring an operator in general does not return a product state.
      * `RemoveMeasured()`, remove the measured qudits from the register. It is also incompatible with the `operator` argument.
  * `operator::AbstractBlock` is the operator to measure.
  * `register::AbstractRegister` is the quantum state.
  * `locs` is the qubits to performance the measurement. If `locs` is not provided, all current active qudits are measured (regarding to active qudits,

see [`focus!`](@ref) and [`relax!`](@ref)).

### Keyword arguments

  * `rng` is the random number generator.

### Examples

The following example measures a random state on the computational basis and reset it to a certain bitstring value.

```jldoctest; setup=:(using Yao, Random; Random.seed!(2))
julia> reg = rand_state(3);

julia> measure!(ResetTo(bit"011"), reg)
110 ₍₂₎

julia> measure(reg; nshots=3)
3-element Vector{DitStr{2, 3, Int64}}:
 011 ₍₂₎
 011 ₍₂₎
 011 ₍₂₎

julia> measure!(RemoveMeasured(), reg, (1,2))
11 ₍₂₎

julia> reg  # removed qubits are not usable anymore
ArrayReg{2, ComplexF64, Array...}
    active qubits: 1/1
    nlevel: 2
```

Measuring an operator will project the state to the subspace associated with the returned eigenvalue.

```jldoctest; setup=:(using Yao, Random; Random.seed!(2))
julia> reg = uniform_state(3)
ArrayReg{2, ComplexF64, Array...}
    active qubits: 3/3
    nlevel: 2

julia> print_table(reg)
000 ₍₂₎   0.35355 + 0.0im
001 ₍₂₎   0.35355 + 0.0im
010 ₍₂₎   0.35355 + 0.0im
011 ₍₂₎   0.35355 + 0.0im
100 ₍₂₎   0.35355 + 0.0im
101 ₍₂₎   0.35355 + 0.0im
110 ₍₂₎   0.35355 + 0.0im
111 ₍₂₎   0.35355 + 0.0im

julia> measure!(repeat(3, Z, 1:3), reg)
-1.0 + 0.0im

julia> print_table(reg)
000 ₍₂₎   0.0 + 0.0im
001 ₍₂₎   0.5 + 0.0im
010 ₍₂₎   0.5 + 0.0im
011 ₍₂₎   0.0 + 0.0im
100 ₍₂₎   0.5 + 0.0im
101 ₍₂₎   0.0 + 0.0im
110 ₍₂₎   0.0 + 0.0im
111 ₍₂₎   0.5 + 0.0im
```

Here, we measured the parity operator, as a result,  the resulting state collapsed to the subspace with either even or odd parity.
