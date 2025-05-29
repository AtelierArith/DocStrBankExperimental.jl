```
infer_bonds!(crystal, include_bonds_across_periodic_boundaries; bonding_rules=rc[:bonding_rules])
```

結晶オブジェクト内の結合を結合ルールに基づいて埋めます。ペアに適切なルールがない場合、それらは結合されていると見なされません。

`:*` はワイルドカードと見なされ、任意の種に置き換えることができます。十分に近い限り、任意の原子が結合できるように、2つの `:*` の間に結合ルールを含めることをお勧めします。

結合ルールは階層的であり、最初の結合ルールが後のものに優先します。

# 引数

  * `crystal::Crystal`: 結合が追加される結晶。
  * `include_bonds_across_periodic_boundaries::Bool`: 結合を計算する際に周期境界を越えてチェックするかどうか。
  * `bonding_rules::Array{BondingRule, 1}`: 結合情報を埋めるために使用される結合ルールの配列。表示される順序で適用されます。提供されていない場合は `rc[:bonding_rules]` が使用されます。
  * `calculate_vectors::Bool`: オプション。`bonds` グラフ内のすべてのエッジにベクトル情報を注釈するには `true` に設定します。
  * `sanity_check::Bool`: オプション。結合を推測した後にサニティチェックをスキップするには `false` に設定します。
