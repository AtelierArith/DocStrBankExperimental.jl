```
get_quoteSummary(symbol::String; item=nothing)
```

Yahoo FinanceからJSON3オブジェクトに保存された一般情報を取得します。

## 引数

  * `symbol::String` はティッカー（例：Apple ComputersのAAPL、またはS&P500の^GSPC）です。
  * `item` は文字列または複数のアイテムを含む`Vector`の`Strings`として指定できます。有効なアイテムを確認するには`_QuoteSummary_Items`を呼び出してください（すべてのアイテムがすべてのタイプの証券で利用できるわけではありません）。
  * `throw_error::Bool` はデフォルトで`false`です。これを`true`に設定すると、ティッカーが無効な場合に関数がエラーを返します。そうでない場合は警告が表示され、空の`JSON3.Object`が返されます。

# 例

```julia-repl
julia> get_quoteSummary("AAPL")

JSON3.Object{Vector{UInt8}, SubArray{UInt64, 1, Vector{UInt64}, Tuple{UnitRange{Int64}}, true}} with 31 entries:
:assetProfile             => {…
:recommendationTrend      => {…
:cashflowStatementHistory => {…

⋮                         => ⋮
julia> get_quoteSummary("AAPL",item = "quoteType")
JSON3.Object{Vector{UInt8}, SubArray{UInt64, 1, Vector{UInt64}, Tuple{UnitRange{Int64}}, true}} with 13 entries:
:exchange               => "NMS"
:quoteType              => "EQUITY"
:symbol                 => "AAPL"
⋮                       => ⋮
```
