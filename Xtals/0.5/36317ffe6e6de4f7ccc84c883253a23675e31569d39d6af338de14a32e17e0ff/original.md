```
infer_bonds!(crystal, include_bonds_across_periodic_boundaries; bonding_rules=rc[:bonding_rules])
```

Populate the bonds in the crystal object based on the bonding rules. If a pair doesn't have a suitable rule then they will not be considered bonded.

`:*` is considered a wildcard and can be substituted for any species. It is a good idea to include a bonding rule between two `:*` to allow any atoms to bond as long as they are close enough.

The bonding rules are hierarchical, i.e. the first bonding rule takes precedence over the latter ones.

# Arguments

  * `crystal::Crystal`: The crystal that bonds will be added to.
  * `include_bonds_across_periodic_boundaries::Bool`: Whether to check across the periodic boundary when calculating bonds.
  * `bonding_rules::Array{BondingRule, 1}`: The array of bonding rules that will be used to fill the bonding information. They are applied in the order that they appear. `rc[:bonding_rules]` will be used if none provided.
  * `calculate_vectors::Bool`: Optional. Set `true` to annotate all edges in the `bonds` graph with vector information.
  * `sanity_check::Bool`: Optional. Set `false` to skip the sanity check after inferring bonds.
