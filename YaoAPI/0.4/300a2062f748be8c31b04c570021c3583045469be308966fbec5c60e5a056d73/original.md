```
focus(f, register, locs)
```

Call a callable `f` under the context of `focus`. See also [`focus!`](@ref).

### Examples

To print the focused register

```jldoctest; setup=:(using Yao)
julia> r = arrayreg(bit"101100")
ArrayReg{2, ComplexF64, Array...}
    active qubits: 6/6
    nlevel: 2

julia> focus(x->(println(x);x), r, (1, 2));
ArrayReg{2, ComplexF64, Array...}
    active qubits: 2/6
    nlevel: 2
```
