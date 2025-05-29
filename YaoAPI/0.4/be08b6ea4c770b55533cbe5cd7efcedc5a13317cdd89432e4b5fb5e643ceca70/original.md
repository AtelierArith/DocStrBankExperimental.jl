```
collapseto!(register, config)
```

Set the `register` to bit string literal `bit_str` (or an equivalent integer). About bit string literal, see more in [`@bit_str`](@ref). This interface is only for emulation.

### Examples

The following code collapse a random state to a certain state.

```jldoctest; setup=:(using Yao)
julia> measure(collapseto!(rand_state(3), bit"001"); nshots=3)
3-element Vector{DitStr{2, 3, Int64}}:
 001 ₍₂₎
 001 ₍₂₎
 001 ₍₂₎
```
