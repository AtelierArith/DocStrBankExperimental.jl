```
get_symbols(search_term::String)
```

Allows searches for specific securities.

# Arguments

  * `search_term::String`: Typically a company/security name (e.g. microsoft)

# Returns

  * A `YahooSearch <: AbstractArray` containing `YahooSearchItem`s containing the following fields: symbol`::String`, shortname`::String`, exchange`::String`, quoteType`::String`, sector`::String`, industry`::String`

# Example

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
