```
Measure{D,K, OT, LT, PT, RNG} <: PrimitiveBlock{D}
Measure(n::Int; rng=Random.GLOBAL_RNG, operator=ComputationalBasis(), locs=1:n, resetto=nothing, remove=false, nlevel=2)
```

Measure operator, currently only qudits are supported.
