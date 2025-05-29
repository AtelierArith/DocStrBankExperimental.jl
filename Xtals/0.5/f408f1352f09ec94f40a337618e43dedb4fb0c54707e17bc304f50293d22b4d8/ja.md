```
write_bonding_rules("file.csv")
```

CSVファイルにボンディングルールを書き込みます。これは[`read_bonding_rules`](@ref)で読み込むことができます。

# 引数

  * `filename::AbstractString` : 出力ファイルの名前
  * `bonding_rules::Array{BondingRule}` : （オプション）ファイルに書き込むルール。指定されていない場合は、グローバルルールが書き込まれます。
