```
get_Fundamental(symbol::AbstractString, item::AbstractString,interval::AbstractString, startdt, enddt)
```

Retrievs financial statement information from Yahoo Finance stored in a OrderedCollections.OrderedDict.

# Arguments

  * `smybol::String` is a ticker (e.g. AAPL for Apple Computers, or ^GSPC for the S&P500)
  * `item::String` can either be an entire financial statement or a subitem. Entire financial statements:`"income_statement", "valuation", "cash_flow", "balance_sheet"`. To see valid sub items grouped by financial statement type in a `OrderedCollections.OrderedDict` call `_Fundamental_Types`
  * `interval::String` can be one of "annual", "quarterly", "monthly"
  * `startdt` and `enddt` take the following types: `::Date`,`::DateTime`, or a `String` of the following form `yyyy-mm-dd`
  * `throw_error::Bool` defaults to `false`. If set to true the function errors when the ticker is not valid. Else a warning is given and an empty `OrderedCollections.OrderedDict` is returned.

# Examples

```julia-repl
julia> get_Fundamental("NFLX", "income_statement","quarterly","2000-01-01","2022-12-31")
OrderedDict{String, Any} with 40 entries:
  "timestamp"                       => [DateTime("2021-12-31T00:00:00"), DateTime("2022-0…  "GeneralAndAdministrativeExpense" => Any[397790000, 397928000, 409297000, 373213000]    
  "SellingGeneralAndAdministration" => Any[1190503000, 953906000, 984257000, 941167000]   
  "InterestIncome"                  => Any[108512000, 195645000, 220226000, 261404000]    
  "OperatingRevenue"                => Any[7709318000, 7867767000, 7970141000, 7925589000]  "DilutedNIAvailtoComStockholders" => Any[607429000, 1597447000, 1440951000, 1398242000] 
  "NormalizedIncome"                => Any[607429000, 1597447000, 1440951000, 1398242000] 
  "NetIncomeCommonStockholders"     => Any[607429000, 1597447000, 1440951000, 1398242000] 
  "BasicAverageShares"              => Any[443462000, 444146000, 444557000, 444878000]    
  ⋮                                 => ⋮


julia> using DataFrames
julia> get_Fundamental("AAPL", "InterestExpense","quarterly","2000-01-01","2022-12-31") |> DataFrame
4×2 DataFrame
 Row │ timestamp            InterestExpense 
     │ DateTime             Any
─────┼──────────────────────────────────────
   1 │ 2021-12-31T00:00:00  694000000
   2 │ 2022-03-31T00:00:00  691000000
   3 │ 2022-06-30T00:00:00  719000000
   4 │ 2022-09-30T00:00:00  827000000
```
