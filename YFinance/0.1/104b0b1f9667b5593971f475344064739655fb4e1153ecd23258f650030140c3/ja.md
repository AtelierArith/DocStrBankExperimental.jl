```
get_institutional_ownership(quoteSummary::JSON3.Object)
```

引用概要から機関投資家の所有権を取得します。

## 引数

`get_quoteSummary(symbol::String; item=nothing,throw_error=false)`から返された`JSON3.Object`または`AbstractString`型のティッカーシンボルのいずれかである必要があります。ティッカーシンボルが提供されると、最初に`get_quoteSummary(symbol::String)`が呼び出されます。

# 例

```julia-repl
julia> get_quoteSummary("AAPL") |> get_institutional_ownership
OrderedDict{String, Vector} with 6 entries:
  "organization" => ["Vanguard Group, Inc. (The)", "Blackrock Inc.", "Berkshire Hathaway,…  
  "reportDate"   => Union{Missing, DateTime}[DateTime("2022-09-30T00:00:00"), DateTime("2…  
  "pctHeld"      => Union{Missing, Float64}[0.08, 0.0641, 0.0562, 0.0372, 0.0221, 0.0176,…  
  "position"     => Union{Missing, Int64}[1272378901, 1020245185, 894802319, 591543874, 3…  
  "value"        => Union{Missing, Int64}[164913030135, 132233979050, 115975329111, 76670…  
  "pctChange"    => Union{Missing, Float64}[-0.0039, -0.0082, 0.0, -0.0111, 0.0191, 0.005…

julia> get_institutional_ownership("AAPL")
OrderedDict{String, Vector} with 6 entries:
  "organization" => ["Vanguard Group, Inc. (The)", "Blackrock Inc.", "Berkshire Hathaway,…  
  "reportDate"   => Union{Missing, DateTime}[DateTime("2022-09-30T00:00:00"), DateTime("2…  
  "pctHeld"      => Union{Missing, Float64}[0.08, 0.0641, 0.0562, 0.0372, 0.0221, 0.0176,…  
  "position"     => Union{Missing, Int64}[1272378901, 1020245185, 894802319, 591543874, 3…  
  "value"        => Union{Missing, Int64}[164913030135, 132233979050, 115975329111, 76670…  
  "pctChange"    => Union{Missing, Float64}[-0.0039, -0.0082, 0.0, -0.0111, 0.0191, 0.005…

julia> using DataFrames
julia> get_institutional_ownership("AAPL") |> DataFrame
10×6 DataFrame
 Row │ organization                   reportDate           pctHeld   position    value   ⋯
     │ String                         DateTime?            Float64?  Int64?      Int64?  ⋯
─────┼────────────────────────────────────────────────────────────────────────────────────
   1 │ Vanguard Group, Inc. (The)     2022-09-30T00:00:00    0.08    1272378901  1649130 ⋯
   2 │ Blackrock Inc.                 2022-09-30T00:00:00    0.0641  1020245185  1322339  
   3 │ Berkshire Hathaway, Inc        2022-09-30T00:00:00    0.0562   894802319  1159753  
   4 │ State Street Corporation       2022-09-30T00:00:00    0.0372   591543874   766700  
   5 │ FMR, LLC                       2022-09-30T00:00:00    0.0221   350900116   454801 ⋯
   6 │ Geode Capital Management, LLC  2022-09-30T00:00:00    0.0176   279758518   362595  
   7 │ Price (T.Rowe) Associates Inc  2022-09-30T00:00:00    0.0141   224863541   291445  
   8 │ Morgan Stanley                 2022-09-30T00:00:00    0.0115   182728771   236834  
   9 │ Northern Trust Corporation     2022-09-30T00:00:00    0.0111   176084862   228223 ⋯
  10 │ Bank of America Corporation    2022-09-30T00:00:00    0.0089   142260591   184383  
                                                                         2 columns omitted
```
