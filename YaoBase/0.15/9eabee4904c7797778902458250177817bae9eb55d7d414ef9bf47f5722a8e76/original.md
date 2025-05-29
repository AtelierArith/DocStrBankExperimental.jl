```
relax!(locs::Int...; to_nactive=nqudits(register)) -> f(register) -> register
```

Lazy version of [`relax!`](@ref), it will be evaluated once you feed a register to its output lambda.
