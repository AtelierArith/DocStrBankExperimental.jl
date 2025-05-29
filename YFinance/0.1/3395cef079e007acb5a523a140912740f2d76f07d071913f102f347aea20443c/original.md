```
get_insider_transactions(quoteSummary::JSON3.Object)
```

Retrievs the insider transactions from the quote summary.

## Arguments

Can be either a `JSON3.Object` returned from `get_quoteSummary(symbol::String; item=nothing,throw_error=false)` or a ticker symbol of type `AbstractString` If a ticker symbol is provided `get_quoteSummary(symbol::String)` is called first. 

# Examples

```julia-repl
julia> get_quoteSummary("AAPL") |> get_insider_transactions
OrderedDict{String, Vector} with 7 entries:
  "filerName"       => ["KONDO CHRISTOPHER", "MAESTRI LUCA", "O'BRIEN DEIRDRE", "KONDO CH…  
  "filerRelation"   => Union{Missing, String}["Officer", "Chief Financial Officer", "Offi…  
  "transactionText" => Union{Missing, String}["Sale at price 148.72 per share.", "Sale at…  
  "date"            => Union{Missing, DateTime}[DateTime("2022-11-22T00:00:00"), DateTime…  
  "ownership"       => Union{Missing, String}["D", "D", "D", "D", "D", "D", "D", "D", "I"…  
  "shares"          => Union{Missing, Int64}[20200, 176299, 8053, 13136, 16612, 181139, 1…  
  "value"           => Union{Missing, Int64}[3004144, 27493275, 1147150, missing, missing…

julia> get_insider_transactions("AAPL")
OrderedDict{String, Vector} with 7 entries:
  "filerName"       => ["KONDO CHRISTOPHER", "MAESTRI LUCA", "O'BRIEN DEIRDRE", "KONDO CH…  
  "filerRelation"   => Union{Missing, String}["Officer", "Chief Financial Officer", "Offi…  
  "transactionText" => Union{Missing, String}["Sale at price 148.72 per share.", "Sale at…  
  "date"            => Union{Missing, DateTime}[DateTime("2022-11-22T00:00:00"), DateTime…  
  "ownership"       => Union{Missing, String}["D", "D", "D", "D", "D", "D", "D", "D", "I"…  
  "shares"          => Union{Missing, Int64}[20200, 176299, 8053, 13136, 16612, 181139, 1…  
  "value"           => Union{Missing, Int64}[3004144, 27493275, 1147150, missing, missing…

julia> using DataFrames
julia> get_insider_transactions("AAPL") |> DataFrame
75×7 DataFrame
 Row │ filerName           filerRelation            transactionText                    d ⋯
     │ String              String?                  String?                            D ⋯
─────┼────────────────────────────────────────────────────────────────────────────────────
   1 │ KONDO CHRISTOPHER   Officer                  Sale at price 148.72 per share.    2 ⋯
   2 │ MAESTRI LUCA        Chief Financial Officer  Sale at price 154.70 - 157.20 pe…  2  
   3 │ O'BRIEN DEIRDRE     Officer                  Sale at price 142.45 per share.    2  
   4 │ KONDO CHRISTOPHER   Officer                                                     2  
   5 │ O'BRIEN DEIRDRE     Officer                                                     2 ⋯   
   6 │ ADAMS KATHERINE L   General Counsel          Sale at price 138.44 - 142.93 pe…  2  
   7 │ O'BRIEN DEIRDRE     Officer                  Sale at price 141.09 - 142.83 pe…  2  
  ⋮  │         ⋮                      ⋮                             ⋮                    ⋱
  70 │ WAGNER SUSAN L      Director                                                    2  
  71 │ JUNG ANDREA         Director                                                    2 ⋯
  72 │ BELL JAMES A        Director                                                    2  
  73 │ LOZANO MONICA C.    Director                                                    2  
  74 │ GORE ALBERT A JR    Director                                                    2  
  75 │ ADAMS KATHERINE L   General Counsel          Sale at price 131.79 - 134.56 pe…  2 ⋯
                                                             4 columns and 62 rows omitted
```
