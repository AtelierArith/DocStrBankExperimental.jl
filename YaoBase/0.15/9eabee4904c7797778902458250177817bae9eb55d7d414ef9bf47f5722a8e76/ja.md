```
relax!(locs::Int...; to_nactive=nqudits(register)) -> f(register) -> register
```

[`relax!`](@ref) の遅延バージョンで、出力ラムダにレジスタを与えると評価されます。
