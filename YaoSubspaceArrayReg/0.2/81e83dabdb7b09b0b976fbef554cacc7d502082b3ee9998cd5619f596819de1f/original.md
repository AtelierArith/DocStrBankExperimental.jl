```
SubspaceArrayReg{D, T, State, Space} <: AbstractArrayReg{D}
SubspaceArrayReg{D}(state, subspace)
SubspaceArrayReg(state, subspace)
```

Type for registers in a subspace. The subspace must be a [`Subspace`](@ref).
