```
formula = empirical_formula(crystal, verbose=false)
```

結晶構造の還元不可能な化学式を見つけます。

# 引数

  * `crystal::Crystal`: 結晶構造情報を含む結晶
  * `verbose::Bool`: `true` の場合、化学式も印刷します

# 戻り値

  * `formula::Dict{Symbol, Int}`: 結晶構造の還元不可能な化学式を持つ辞書
