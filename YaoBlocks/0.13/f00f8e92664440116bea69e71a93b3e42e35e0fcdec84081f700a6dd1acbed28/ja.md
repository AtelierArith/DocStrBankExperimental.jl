```
single_qubit_depolarizing_channel(p::Real)
```

単一量子ビットの脱極化チャネルを作成します。

pの前の3/4の係数は、 `single_qubit_depolarizing_channel(p) == depolarizing_channel(1, p)` であることを保証します。

$$
(1 - 3p/4 ⋅ρ) + p/4⋅(XρX + YρY + ZρZ)
$$
