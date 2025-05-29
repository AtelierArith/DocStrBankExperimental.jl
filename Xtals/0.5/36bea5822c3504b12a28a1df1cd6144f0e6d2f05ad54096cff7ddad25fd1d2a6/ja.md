```
ρ = crystal_density(crystal) # kg/m²
```

結晶の結晶密度を計算します。[`read_atomic_masses`](@ref)から原子量を取得します。

# 引数

  * `crystal::Crystal`: 結晶構造情報を含む結晶

# 戻り値

  * `ρ::Float64`: kg/m³での結晶の結晶密度  # –> kg/m3
