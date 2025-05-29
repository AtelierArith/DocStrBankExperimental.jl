```
single_qubit_depolarizing_channel(p::Real)
```

Create a single-qubit depolarizing channel.

The factor of 3/4 in front of p ensures that  `single_qubit_depolarizing_channel(p) == depolarizing_channel(1, p)`

$$
(1 - 3p/4 ⋅ρ) + p/4⋅(XρX + YρY + ZρZ)
$$
