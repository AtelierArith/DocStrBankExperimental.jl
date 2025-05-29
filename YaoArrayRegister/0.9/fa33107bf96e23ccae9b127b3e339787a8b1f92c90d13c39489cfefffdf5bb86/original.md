```
normalize!(r::AbstractArrayReg)
```

Normalize the register `r` by its 2-norm. It changes the register directly.

### Examples

The following code creates a normalized GHZ state.

```julia
julia> reg = product_state(bit"000") + product_state(bit"111");

julia> norm(reg)
1.4142135623730951

julia> isnormalized(reg)
false

julia> normalize!(reg);

julia> isnormalized(reg)
true
```
