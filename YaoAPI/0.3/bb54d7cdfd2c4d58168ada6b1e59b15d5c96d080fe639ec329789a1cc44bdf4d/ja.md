```
measure([, operator], register[, locs]; nshots=1, rng=Random.GLOBAL_RNG) -> Vector{Int}
```

`locs` における qudit の測定結果を返します。`locs` が提供されていない場合、すべての現在のアクティブな qudit が測定されます（アクティブな qudit に関しては、[`focus!`](@ref) および [`relax!`](@ref) を参照してください）。
