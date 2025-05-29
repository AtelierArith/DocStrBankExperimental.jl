```
get_Options(symbol::String)
```

Yahoo Financeからオプションデータを取得し、2つのアイテムを持つOrderedCollections.OrderedDictに格納します。1つはコールオプション、もう1つはプットオプションを含みます。これらのサブアイテムもOrderedCollections.OrderedDictです。コールオプションとプットオプションのOrderedCollections.OrderedDictは、簡単にDataFrameに変換できます。

# 引数

  * `symbol::String` はティッカー（例：Apple ComputersのAAPL、またはS&P500の^GSPC）です。
  * `throw_error::Bool` はデフォルトで`false`です。これを`true`に設定すると、ティッカーが無効な場合に関数がエラーを返します。そうでない場合は警告が表示され、空のOrderedCollections.OrderedDictが返されます。

# 例

```julia-repl
julia> get_Options("AAPL")
OrderedDict{String, OrderedDict{String, Vector{Any}}} with 2 entries:
  "calls" => OrderedDict("contractSymbol"=>["AAPL221230C00050000", "AAPL221230C00055000",…
  "puts"  => OrderedDict("contractSymbol"=>["AAPL221230P00050000", "AAPL221230P00055000",…

julia> using DataFrames
julia> get_Options("AAPL")["calls"] |> DataFrame
72×16 DataFrame
 Row │ contractSymbol       strike  currency  lastPrice  change  percentChange  volume   ⋯
     │ Any                  Any     Any       Any        Any     Any            Any      ⋯
─────┼────────────────────────────────────────────────────────────────────────────────────
   1 │ AAPL221230C00050000  50      USD       79.85      0       0              1        ⋯
   2 │ AAPL221230C00055000  55      USD       72.85      0       0              1
   3 │ AAPL221230C00060000  60      USD       66.4       0       0              19        
  ⋮  │          ⋮             ⋮        ⋮          ⋮        ⋮           ⋮           ⋮     ⋱
  71 │ AAPL221230C00230000  230     USD       0.02       0       0              missing   
  72 │ AAPL221230C00250000  250     USD       0.01       0       0              2        ⋯
                                                             9 columns and 67 rows omitted

julia> using DataFrames
julia> data  = get_Options("AAPL");
julia> vcat( [DataFrame(i) for i in values(data)]...)
141×16 DataFrame
 Row │ contractSymbol       strike  currency  lastPrice  change  percentChange  volume   ⋯
     │ Any                  Any     Any       Any        Any     Any            Any      ⋯
─────┼────────────────────────────────────────────────────────────────────────────────────
   1 │ AAPL221230C00050000  50      USD       79.85      0       0              1        ⋯
   2 │ AAPL221230C00055000  55      USD       72.85      0       0              1
   3 │ AAPL221230C00060000  60      USD       66.4       0       0              19        
  ⋮  │          ⋮             ⋮        ⋮          ⋮        ⋮           ⋮          ⋮      ⋱
 140 │ AAPL221230P00225000  225     USD       94.65      0       0              1
 141 │ AAPL221230P00230000  230     USD       99.65      0       0              1        ⋯
                                                            9 columns and 136 rows omitted
```
