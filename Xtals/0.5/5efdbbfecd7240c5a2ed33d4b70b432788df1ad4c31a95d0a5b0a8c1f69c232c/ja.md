```
bonding_rule = BondingRule(:Ca, :O, 2.0)
bonding_rules = [BondingRule(:H, :*, 1.2),
                 BondingRule(:*, :*, 1.9)]
```

結晶内の2つの原子が結合しているかどうかを判断するためのルール。

# 属性

  * `species_i::Symbol`: この結合ルールのための原子の1つのタイプ
  * `species_j::Symbol`: この結合ルールのためのもう1つの原子タイプ
  * `max_dist`: 結合が発生するための原子間の最大距離
