```
read_bonding_rules("file.csv")
```

CSVファイルの結合ルールを読み込み、BondingRule配列を返します。

# 引数

  * `filename::AbstractString` : 結合ルールを含むデータディレクトリ内のファイル名

# 戻り値

`rules::Array{BondingRule}` : ファイルから読み込まれた結合ルール
