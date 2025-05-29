```julia
projector(
    v::YaoArrayRegister.AbstractArrayReg
) -> YaoBlocks.Projector

```

Create a [`Projector`](@ref) with an quantum state vector `v`.

### Example

```jldoctest; setup=:(using YaoBlocks, YaoArrayRegister)
julia> projector(rand_state(3))
|s⟩⟨s|, nqudits = 3
```
