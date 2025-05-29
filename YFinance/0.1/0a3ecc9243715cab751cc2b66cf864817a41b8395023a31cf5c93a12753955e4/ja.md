```
get_major_holders_breakdown(quoteSummary::JSON3.Object)
```

引用要約から主要保有者の内訳を取得します。

## 引数

`get_quoteSummary(symbol::String; item=nothing,throw_error=false)` から返された `JSON3.Object` か、`AbstractString` 型のティッカーシンボルのいずれかです。ティッカーシンボルが提供された場合、最初に `get_quoteSummary(symbol::String)` が呼び出されます。

# 例

```julia-repl
julia> get_quoteSummary("AAPL") |> get_major_holders_breakdown
OrderedDict{String, Real} with 4 entries:  
  "insidersPercentHeld"          => 0.00072
  "institutionsPercentHeld"      => 0.60915
  "institutionsFloatPercentHeld" => 0.60959
  "institutionsCount"            => 5526  

julia> get_major_holders_breakdown("AAPL")
OrderedDict{String, Real} with 4 entries:  
  "insidersPercentHeld"          => 0.00072
  "institutionsPercentHeld"      => 0.60915
  "institutionsFloatPercentHeld" => 0.60959
  "institutionsCount"            => 5526
```
