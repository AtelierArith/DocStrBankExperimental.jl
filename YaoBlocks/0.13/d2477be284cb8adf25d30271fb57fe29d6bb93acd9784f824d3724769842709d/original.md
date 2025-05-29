```
pauli_error_channel(; px::Real, py::Real=px, pz::Real=px)
```

Create the Pauli error channel as a [`UnitaryChannel`](@ref)

$$
    (1 - (p_x + p_y + p_z))⋅ρ + p_x⋅XρX + p_y⋅YρY  + p_z⋅ZρZ
$$
