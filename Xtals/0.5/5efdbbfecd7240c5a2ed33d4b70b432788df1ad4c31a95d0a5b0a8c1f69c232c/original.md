```
bonding_rule = BondingRule(:Ca, :O, 2.0)
bonding_rules = [BondingRule(:H, :*, 1.2),
                 BondingRule(:*, :*, 1.9)]
```

A rule for determining if two atoms within a crystal are bonded.

# Attributes

  * `species_i::Symbol`: One of the atoms types for this bond rule
  * `species_j::Symbol`: The other atom type for this bond rule
  * `max_dist`: The maximum distance between the atoms for bonding to occur
