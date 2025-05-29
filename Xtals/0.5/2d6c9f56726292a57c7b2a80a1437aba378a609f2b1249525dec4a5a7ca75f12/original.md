```
replicated_crystal = replicate(crystal, repfactors)
```

replicate the atoms and charges in a `Crystal` in positive directions to construct a new `Crystal`. Note `replicate(crystal, (1, 1, 1))` returns the same `Crystal`. the fractional coordinates will be rescaled to be in [0, 1].

# arguments

  * `crystal::Crystal`: The crystal to replicate
  * `repfactors::Tuple{Int, Int, Int}`: The factors by which to replicate the crystal structure in each crystallographic direction (a, b, c).

# returns

  * `replicated_frame::Crystal`: replicated crystal
