```
phase(theta)
```

Returns a global phase gate. Defined with following matrix form:

$$
e^{iθ} I
$$

### Examples

You can create a global phase gate with a phase (a real number).

```jldoctest; setup=:(using YaoBlocks)
julia> phase(0.1)
phase(0.1)
```
