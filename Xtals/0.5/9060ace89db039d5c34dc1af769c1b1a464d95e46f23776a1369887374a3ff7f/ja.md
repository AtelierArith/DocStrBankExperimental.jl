```
mass_of_crystal = molecular_weight(crystal)
```

結晶の単位セルの分子量をamuで計算します。情報は`data/atomicmasses.csv`に保存されています。

# 引数

  * `crystal::Crystal`: 結晶構造情報を含む結晶

# 戻り値

  * `mass_of_crystal::Float64`: 結晶の単位セルの分子量（amu単位）
