```
occupied_locs(x)
```

Return a tuple of occupied locations of `x`.

### Examples

```jldoctest; setup=:(using Yao)
julia> occupied_locs(kron(5, 1=>X, 3=>X))
(1, 3)

julia> occupied_locs(kron(5, 1=>X, 3=>I2))
(1,)
```
