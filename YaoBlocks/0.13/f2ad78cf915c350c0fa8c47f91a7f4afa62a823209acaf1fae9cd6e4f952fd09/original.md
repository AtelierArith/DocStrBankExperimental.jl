```
OnLevels{D, Ds, T <: AbstractBlock{Ds}} <: TagBlock{T, D}
```

Define a gate that is applied to a subset of levels.

### Fields

  * `gate`: the gate to be applied.
  * `levels`: the levels to apply the gate to.
