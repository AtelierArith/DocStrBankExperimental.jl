```
measure([, operator], register[, locs]; nshots=1, rng=Random.GLOBAL_RNG) -> Vector{Int}
```

Return measurement results of qudits in `locs`. If `locs` is not provided, all current active qudits are measured (regarding to active qudits, see [`focus!`](@ref) and [`relax!`](@ref)).
