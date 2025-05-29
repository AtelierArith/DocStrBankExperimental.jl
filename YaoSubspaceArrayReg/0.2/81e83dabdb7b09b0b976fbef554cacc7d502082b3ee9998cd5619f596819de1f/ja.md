```
SubspaceArrayReg{D, T, State, Space} <: AbstractArrayReg{D}
SubspaceArrayReg{D}(state, subspace)
SubspaceArrayReg(state, subspace)
```

サブスペース内のレジスタの型。サブスペースは[`Subspace`](@ref)でなければなりません。
