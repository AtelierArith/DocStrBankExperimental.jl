```
get_Options(symbol::String)
```

Retrievs options data from Yahoo Finance stored in a OrderedCollections.OrderedDict with two items. One contains Call options the other Put options. These subitems are OrderedCollections.OrderedDict themselves. The call and put options OrderedCollections.OrderedDict can readily be transformed to a DataFrame.

# Arguments

  * smybol`::String` is a ticker (e.g. AAPL for Apple Computers, or ^GSPC for the S&P500)
  * throw_error`::Bool` defaults to `false`. If set to true the function errors when the ticker is not valid. Else a warning is given and an empty OrderedCollections.OrderedDict is returned.

# Examples

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
