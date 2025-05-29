```
read_bonding_rules("file.csv")
```

Reads a CSV file of bonding rules and returns a BondingRule array.

# Arguments

  * `filename::AbstractString` : name of file in data directory containing bonding rules

# Returns

`rules::Array{BondingRule}` : the bonding rules read from file
