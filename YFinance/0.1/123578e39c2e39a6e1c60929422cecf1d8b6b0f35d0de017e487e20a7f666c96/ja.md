```
get_eps(quoteSummary::JSON3.Object)
```

引用要約から1株あたりの利益を取得します。

## 引数

`get_quoteSummary(symbol::String; item=nothing,throw_error=false)`から返された`JSON3.Object`または`AbstractString`型のティッカーシンボルのいずれかである必要があります。ティッカーシンボルが提供された場合、最初に`get_quoteSummary(symbol::String)`が呼び出されます。

# 例

```julia-repl
julia> get_quoteSummary("AAPL") |> get_eps
OrderedDict{String, Vector} with 4 entries:
  "quarter"  => [DateTime("2021-12-31T00:00:00"), DateTime("2022-03-31T00:00:00"), DateTime("2022-06-30T00:00:00"), DateTime("2022-09-30T00:00:00")]
  "estimate" => [1.89, 1.43, 1.16, 1.27]
  "actual"   => [2.1, 1.52, 1.2, 1.29]
  "surprise" => [0.111, 0.063, 0.034, 0.016]

julia> get_eps("AAPL")
OrderedDict{String, Vector} with 4 entries:
  "quarter"  => [DateTime("2021-12-31T00:00:00"), DateTime("2022-03-31T00:00:00"), DateTime("2022-06-30T00:00:00"), DateTime("2022-09-30T00:00:00")]
  "estimate" => [1.89, 1.43, 1.16, 1.27]
  "actual"   => [2.1, 1.52, 1.2, 1.29]
  "surprise" => [0.111, 0.063, 0.034, 0.016]

julia> using DataFrames
julia> get_eps("AAPL") |> DataFrame
4×4 DataFrame
 Row │ quarter              estimate  actual   surprise 
     │ DateTime             Float64   Float64  Float64  
─────┼──────────────────────────────────────────────────
   1 │ 2021-12-31T00:00:00      1.89     2.1      0.111
   2 │ 2022-03-31T00:00:00      1.43     1.52     0.063
   3 │ 2022-06-30T00:00:00      1.16     1.2      0.034
   4 │ 2022-09-30T00:00:00      1.27     1.29     0.016
```
