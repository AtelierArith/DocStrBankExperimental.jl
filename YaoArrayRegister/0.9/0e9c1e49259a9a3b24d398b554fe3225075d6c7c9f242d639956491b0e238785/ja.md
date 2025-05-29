```
von_neumann_entropy(reg::AbstractArrayReg, part)
von_neumann_entropy(ρ::DensityMatrix)
```

量子状態 `reg` における `part` と残りの部分との間のエンタングルメントエントロピー。入力が密度行列の場合、混合状態のエントロピーを返します。

### 例

GHZ状態の任意のセグメントのフォン・ノイマンエントロピーは $\log 2$ です。

```jldoctest; setup=:(using Yao)
julia> von_neumann_entropy(ghz_state(3), (1,2))
0.6931471805599612
```
