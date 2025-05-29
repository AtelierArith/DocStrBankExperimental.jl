```
select!(dest::AbstractRegister, src::AbstractRegister, bits::Integer...) -> AbstractRegister
select!(register::AbstractRegister, bits::Integer...) -> register
```

select a subspace of given quantum state based on input eigen state `bits`. See also [`select`](@ref).

## Example

`select!(reg, 0b110)` will select the subspace with (focused) configuration `110`. After selection, the focused qubit space is 0, so you may want call `relax!` manually.

!!! tip
    Developers should overload `select!(r::RegisterType, bits::NTuple{N, <:Integer})` and do not assume `bits` has specific number of bits (e.g `Int64`), or it will restrict the its maximum available number of qudits.

