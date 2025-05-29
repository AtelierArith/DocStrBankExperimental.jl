```
oneto(n::Int) -> f(register)
oneto(r::AbstractArrayReg, n::Int=nqudits(r))
```

Returns an register with `1:n` qudits activated, which is faster than the general purposed [`focus`](@ref) function.
