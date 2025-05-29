```
bonds = infer_bonds(atoms; bonding_rules=rc[:bonding_rules])
```

原子間の化学結合をエンコードした `MetaGraph` を返します。

# 引数

  * `atoms::Atoms{Cart}`: 結合する原子
  * `bonding_rules::Vector{BondingRule}`: 使用する結合ルール
