```
get_ESG(symbol::String)
```

Yahoo FinanceからESGスコアを取得し、2つのアイテムを持つOrderedCollections.OrderedDictに格納します。一つは`score`で、企業のESGスコアと個別の総合、環境、社会、ガバナンススコア、および`DateTime`型のタイムスタンプを含みます。もう一つは`peer_score`で、ピアグループのスコアを含みます。サブ辞書は`DataFrames`に変換できます。

# 引数

  * `symbol::String`はティッカー（例：Apple ComputersのAAPLや、S&P500の^GSPC）です。
  * `throw_error::Bool`はデフォルトで`false`です。これを`true`に設定すると、ティッカーが無効な場合に関数がエラーを返します。そうでない場合は警告が表示され、空のOrderedCollections.OrderedDictが返されます。

# 例

```julia-repl
julia> get_ESG("AAPL")
OrderedDict{String, OrderedDict{String, Any}} with 2 entries:
  "score"      => OrderedDict("symbol"=>"AAPL", "timestamp"=>[DateTime("2014-09-01T00:00:…
  "peer_score" => OrderedDict("symbol"=>"Technology Hardware", "timestamp"=>[DateTime("20…

julia> using DataFrames
julia> get_ESG("AAPL")["score"] |> DataFrame
96×6 DataFrame
 Row │ symbol  timestamp            esgScore    governanceScore  environmentScore  socialScore 
     │ String  DateTime             Real?       Real?            Real?             Real?       
─────┼─────────────────────────────────────────────────────────────────────────────────────────
   1 │ AAPL    2014-09-01T00:00:00       61               62                74           45
   2 │ AAPL    2014-10-01T00:00:00       60               62                74           45
   3 │ AAPL    2014-11-01T00:00:00       61               62                74           45
  ⋮  │   ⋮              ⋮               ⋮              ⋮                ⋮               ⋮
  95 │ AAPL    2022-07-01T00:00:00  missing          missing           missing      missing    
  96 │ AAPL    2022-08-01T00:00:00       16.68             9.18              0.65         6.86
                                                                                91 rows omitted
```
