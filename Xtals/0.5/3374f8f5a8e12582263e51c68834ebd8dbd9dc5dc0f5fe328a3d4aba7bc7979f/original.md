```
formula = empirical_formula(crystal, verbose=false)
```

Find the irreducible chemical formula of a crystal structure.

# Arguments

  * `crystal::Crystal`: The crystal containing the crystal structure information
  * `verbose::Bool`: If `true`, will print the chemical formula as well

# Returns

  * `formula::Dict{Symbol, Int}`: A dictionary with the irreducible chemical formula of a crystal structure
