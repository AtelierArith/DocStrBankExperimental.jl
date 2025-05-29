```
get_symbols(search_term::String)
```

特定の証券を検索することを可能にします。

# 引数

  * `search_term::String`: 通常は企業/証券名（例: microsoft）

# 戻り値

  * `YahooSearch <: AbstractArray` は、次のフィールドを含む `YahooSearchItem` を含みます: symbol`::String`, shortname`::String`, exchange`::String`, quoteType`::String`, sector`::String`, industry`::String`

# 例

```julia
julia> get_symbols("micro")
7-element YahooSearch{YahooSearchItem, 1}:
 
Symbol:  MGC=F
Name:    Micro Gold Futures,Jun-2023
Type:    FUTURE
Exch.:   New York Commodity Exchange (CMX)


Symbol:  MSFT
Name:    Microsoft Corporation
Type:    EQUITY
Exch.:   NASDAQ (NMS)
Sec.:    Technology
Ind.:    Software—Infrastructure


Symbol:  AMD
Name:    Advanced Micro Devices, Inc.
Type:    EQUITY
Exch.:   NASDAQ (NMS)
Sec.:    Technology
Ind.:    Semiconductors


Symbol:  MU
Name:    Micron Technology, Inc.
Type:    EQUITY
Exch.:   NASDAQ (NMS)
Sec.:    Technology
Ind.:    Semiconductors


Symbol:  MSTR
Name:    MicroStrategy Incorporated
Type:    EQUITY
Exch.:   NASDAQ (NMS)
Sec.:    Technology
Ind.:    Software—Application


Symbol:  SMCI
Name:    Super Micro Computer, Inc.
Type:    EQUITY
Exch.:   NASDAQ (NMS)
Sec.:    Technology
Ind.:    Computer Hardware


Symbol:  FNGU
Name:    MicroSectors FANG  Index 3X Lev
Type:    ETF
Exch.:   NYSEArca (PCX)
```
