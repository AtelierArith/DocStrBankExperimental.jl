```
bond_rules = bondingrules()
bond_rules = bondingrules(covalent_radii=covalent_radii(), pad=0.05)
```

与えられたコルデロパラメータと許容範囲に基づいて、一連の結合ルールを返します。

# 引数

  * `cov_rad::Union{Dict{Symbol, Float64}, Nothing}`: 共有半径。[`covalent_radii()`](@ref)を参照してください。
  * `pad::Float`: 結合相互作用のために共有半径をパッドする量。

# 戻り値

  * `bondingrules::Array{BondingRule, 1}`: 指定された共有半径からの結合ルール。`
