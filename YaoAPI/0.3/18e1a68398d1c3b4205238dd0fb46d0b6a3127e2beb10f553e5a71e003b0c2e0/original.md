```
focus(f, register, locs...)
```

Call a callable `f` under the context of `focus`. See also [`focus!`](@ref).

# Example

print the focused register

```julia
julia> r = ArrayReg(bit"101100")
ArrayReg{1,Complex{Float64},Array...}
    active qudits: 6/6

julia> focus(x->(println(x);x), r, 1, 2);
ArrayReg{1,Complex{Float64},Array...}
    active qudits: 2/6
```
