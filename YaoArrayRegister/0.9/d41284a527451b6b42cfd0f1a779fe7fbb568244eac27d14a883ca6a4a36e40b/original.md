```
statevec(r::ArrayReg) -> array
```

Return a state matrix/vector by droping the last dimension of size 1 (i.e. `nactive(r) = nqudits(r)`). See also [`state`](@ref).

!!! warning
    `statevec` is not type stable. It may cause performance slow down.

