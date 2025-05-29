```
get_recommendation_trend(quoteSummary::JSON3.Object)
```

引用の要約から推奨トレンドを取得します。

## 引数

`get_quoteSummary(symbol::String; item=nothing,throw_error=false)` から返された `JSON3.Object` か、`AbstractString` 型のティッカーシンボルのいずれかです。ティッカーシンボルが提供された場合、最初に `get_quoteSummary(symbol::String)` が呼び出されます。

# 例

```julia-repl
julia> get_quoteSummary("AAPL") |> get_recommendation_trend
OrderedDict{String, Vector} with 6 entries:
  "period"     => ["0m", "-1m", "-2m", "-3m"]
  "strongbuy"  => [11, 11, 11, 13]
  "buy"        => [21, 25, 26, 20]
  "hold"       => [6, 6, 5, 8]
  "sell"       => [0, 1, 1, 0]
  "strongsell" => [0, 0, 0, 0]

julia> get_recommendation_trend("AAPL")
OrderedDict{String, Vector} with 6 entries:
  "period"     => ["0m", "-1m", "-2m", "-3m"]
  "strongbuy"  => [11, 11, 11, 13]
  "buy"        => [21, 25, 26, 20]
  "hold"       => [6, 6, 5, 8]
  "sell"       => [0, 1, 1, 0]
  "strongsell" => [0, 0, 0, 0]
  
julia> using DataFrames
julia> get_recommendation_trend("AAPL") |> DataFrame
4×6 DataFrame
 Row │ period  strongbuy  buy    hold   sell   strongsell 
     │ String  Int64      Int64  Int64  Int64  Int64      
─────┼────────────────────────────────────────────────────
   1 │ 0m             11     21      6      0           0
   2 │ -1m            11     25      6      1           0
   3 │ -2m            11     26      5      1           0
   4 │ -3m            13     20      8      0           0
```
