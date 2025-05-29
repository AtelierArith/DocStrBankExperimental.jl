```
get_Fundamental(symbol::AbstractString, item::AbstractString,interval::AbstractString, startdt, enddt)
```

Yahoo FinanceからOrderedCollections.OrderedDictに保存された財務諸表情報を取得します。

# 引数

  * `smybol::String` はティッカー（例：Apple ComputersのAAPL、またはS&P500の^GSPC）です。
  * `item::String` は財務諸表全体またはサブアイテムのいずれかです。財務諸表全体：`"income_statement", "valuation", "cash_flow", "balance_sheet"`。財務諸表タイプごとにグループ化された有効なサブアイテムを`OrderedCollections.OrderedDict`で確認するには、`_Fundamental_Types`を呼び出してください。
  * `interval::String` は "annual", "quarterly", "monthly" のいずれかです。
  * `startdt` と `enddt` は次の型を取ります：`::Date`,`::DateTime`、または次の形式の`String` `yyyy-mm-dd`。
  * `throw_error::Bool` はデフォルトで`false`です。これを`true`に設定すると、ティッカーが無効な場合に関数がエラーを返します。そうでない場合は警告が表示され、空の`OrderedCollections.OrderedDict`が返されます。

# 例

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
