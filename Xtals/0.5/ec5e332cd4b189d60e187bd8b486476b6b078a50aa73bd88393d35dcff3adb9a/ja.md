```
crystal_with_charges = assign_charges(crystal, species_to_charge, net_charge_tol=1e-5)
```

原子の種類に基づいて結晶内の原子に電荷を割り当てます。原子種を電荷にマッピングする辞書 `species_to_charge` を渡します。

結晶にすでに電荷がある場合、電荷は削除され、新しい電荷が追加されます。この場合、警告が表示されます。

最後に電荷の中立性をチェックします。

新しい結晶を返します。

# 例

```
species_to_charge = Dict(:Ca => 2.0, :C => 1.0, :H => -1.0)
crystal_with_charges = assign_charges(crystal, species_to_charge, 1e-7)
crystal_with_charges = assign_charges(crystal, species_to_charge) # tol 1e-5 デフォルト
```

# 引数

  * `crystal::Crystal`: 結晶
  * `species_to_charge::Dict{Symbol, Float64}`: 原子種を電荷にマッピングする辞書
  * `net_charge_tol::Float64`: 結果の結晶の電荷中立性を主張する際に許容されるネット電荷
