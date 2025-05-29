```
validate_symbol(symbol::AbstractString)
```

Validates a Symbol (Ticker). Returns `true` if the ticker is valid and `false` if the ticker is not valid.

# Arguments

  * smybol`::String` is a ticker (e.g. AAPL for Apple Computers, or ^GSPC for the S&P500)

# How it works

Checks if the HTTP request works (status 200) or whether the request errors (common status in this case: 404)    
