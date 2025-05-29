```
@bra_str
```

Create a bra register. See also [`@ket_str`](@ref).

### Examples

Similar to `@ket_str` literal, a symbolic quantum state can be created by

```jldoctest; setup=:(using Yao)
julia> bra"111" + 2bra"101"
2.0⟨101| + ⟨111|

julia> bra"111" * (ket"101" + ket"111")
1
```
