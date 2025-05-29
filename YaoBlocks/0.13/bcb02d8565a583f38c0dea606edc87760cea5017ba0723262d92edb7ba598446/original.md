```
Measure(n::Int; rng=Random.GLOBAL_RNG, operator=ComputationalBasis(), locs=AllLocs(), resetto=nothing, remove=false)
```

Create a `Measure` block with number of qudits `n`.

### Examples

You can create a `Measure` block on given basis (default is the computational basis).

```jldoctest; setup=:(using Yao)
julia> Measure(4)
Measure(4)
```

Or you could specify which qudits you are going to measure

```jldoctest; setup=:(using Yao)
julia> Measure(4; locs=1:3)
Measure(4;locs=(1, 2, 3))
```

by default this will collapse the current register to measure results.

```jldoctest; setup=:(using Yao, Random; Random.seed!(123))
julia> r = normalize!(arrayreg(bit"000") + arrayreg(bit"111"))
ArrayReg{2, ComplexF64, Array...}
    active qubits: 3/3
    nlevel: 2

julia> state(r)
8×1 Matrix{ComplexF64}:
 0.7071067811865475 + 0.0im
                0.0 + 0.0im
                0.0 + 0.0im
                0.0 + 0.0im
                0.0 + 0.0im
                0.0 + 0.0im
                0.0 + 0.0im
 0.7071067811865475 + 0.0im

julia> r |> Measure(3)
ArrayReg{2, ComplexF64, Array...}
    active qubits: 3/3
    nlevel: 2

julia> state(r)
8×1 Matrix{ComplexF64}:
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 0.0 + 0.0im
 1.0 + 0.0im
```

But you can also specify the target bit configuration you want to collapse to with keyword `resetto`.

```jldoctest; setup=:(using Yao) julia> m = Measure(4; resetto=bit"0101") Measure(4;postprocess=ResetTo{BitStr{4,Int64}}(0101 ₍₂₎))

julia> m.postprocess ResetTo{BitStr{4,Int64}}(0101 ₍₂₎)```
