```
LibGit2.push!(w::GitRevWalker, cid::GitHash)
```

Inicia el [`GitRevWalker`](@ref) `walker` en el commit `cid`. Esta función se puede usar para aplicar una función a todos los commits desde un cierto año, pasando el primer commit de ese año como `cid` y luego pasando el resultado `w` a [`LibGit2.map`](@ref).
