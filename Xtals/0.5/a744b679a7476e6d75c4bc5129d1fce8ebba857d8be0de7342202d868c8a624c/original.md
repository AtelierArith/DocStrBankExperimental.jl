```
bonds = infer_bonds(atoms; bonding_rules=rc[:bonding_rules])
```

Returns a `MetaGraph` encoding the chemical bonds between atoms.

# Arguments

  * `atoms::Atoms{Cart}`: the atoms to bond
  * `bonding_rules::Vector{BondingRule}`: the bonding rules to use
