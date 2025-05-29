```
new_box = replicate(original_box, repfactors)
```

Replicates a `Box` in positive directions to construct a new `Box` representing a supercell. The `original_box` is replicated according to the factors in `repfactors`. Note `replicate(original_box, repfactors=(1, 1, 1))` returns same `Box`. The new fractional coordinates as described by `f_to_c` and `c_to_f` still ∈ [0, 1].

# Arguments

  * `original_box::Box`: The box that you want to replicate
  * `repfactors::Tuple{Int, Int, Int}`: The factor you want to replicate the box by

# Returns

  * `box::Box`: Fully formed Box object
