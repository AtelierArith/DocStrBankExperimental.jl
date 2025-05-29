```
write_bonding_rules("file.csv")
```

Writes bonding rules to a CSV file that can be loaded with [`read_bonding_rules`](@ref)

# Arguments

  * `filename::AbstractString` : The name of the output file
  * `bonding_rules::Array{BondingRule}` : (Optional) The rules to write to file. If not specified, the global rules are written.
