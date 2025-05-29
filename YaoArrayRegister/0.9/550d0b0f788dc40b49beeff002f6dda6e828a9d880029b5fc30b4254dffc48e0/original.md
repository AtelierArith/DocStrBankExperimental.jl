```julia
isseparable(
    reg::YaoArrayRegister.AbstractArrayReg{D},
    locs
) -> Any

```

Returns true if qudits at `locs` are seperable from the rest qudits. A state $|ψ⟩$ is separable if

$$
|\psi\rangle = |a\rangle \otimes |b\rangle
$$

where $|a⟩$ is defined on the state space at `locs`.

### Examples

```jldoctest; setup=:(using YaoArrayRegister)
julia> isseparable(product_state(bit"01100"), 1:2)
true

julia> isseparable(ghz_state(5), 1:2)
false
```
