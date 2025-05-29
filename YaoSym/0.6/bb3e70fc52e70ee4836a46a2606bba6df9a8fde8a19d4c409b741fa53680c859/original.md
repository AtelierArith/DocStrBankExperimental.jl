```
@ket_str
```

Create a ket register. See also [`@bra_str`](@ref).

### Examples

a symbolic quantum state can be created simply by

```jldoctest; setup=:(using Yao)
julia> ket"110" + 2ket"111"
|110⟩ + 2.0|111⟩
```

qubits can be partially actived by [`focus!`](@ref)

```jldoctest; setup=:(using Yao)
julia> ket"100" + ket"111" |> focus!(1:2)
|100⟩ + |111⟩
```
