```julia
most_probable(
    reg::YaoArrayRegister.ArrayReg{D, T} where T,
    n::Int64
) -> Any

```

Find `n` most probable qubit configurations in a quantum register and return these configurations as a vector of `DitStr` instances.

### Example

```jldoctest; setup=:(using Yao)
julia> most_probable(ghz_state(3), 2)
2-element Vector{DitStr{2, 3, Int64}}:
 000 ₍₂₎
 111 ₍₂₎
```
