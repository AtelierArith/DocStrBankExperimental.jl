```
mutual_information(register_or_rho, part1, part2)
```

入力された量子レジスタまたは密度行列の部分系 `part1` と `part2` の間の相互情報量を返します：

$$
S(\rho_A) + S(\rho_B) - S(\rho_{AB})
$$

### 例

任意の2つの非重複部分のGHZ状態の相互情報量は常に $\log 2$ に等しいです。

```jldoctest; setup=:(using Yao)
julia> mutual_information(ghz_state(4), (1,), (3,4))
0.6931471805599132
```
