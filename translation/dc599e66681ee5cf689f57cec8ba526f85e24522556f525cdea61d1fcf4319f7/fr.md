```
GenericMemory{kind::Symbol, T, addrspace=Core.CPU} <: DenseVector{T}
```

Taille fixe [`DenseVector{T}`](@ref DenseVector).

`kind` peut actuellement être soit `:not_atomic` soit `:atomic`. Pour des détails sur ce que cela implique, voir [`AtomicMemory`](@ref)

`addrspace` ne peut actuellement être défini que sur Core.CPU. Il est conçu pour permettre l'extension par d'autres systèmes tels que les GPU, qui pourraient définir des valeurs telles que :

```
module CUDA
const Generic = bitcast(Core.AddrSpace{CUDA}, 0)
const Global = bitcast(Core.AddrSpace{CUDA}, 1)
end
```

La sémantique exacte de ces autres addrspaces est définie par le backend spécifique, mais générera une erreur si l'utilisateur tente d'y accéder sur le CPU.

!!! compat "Julia 1.11"
    Ce type nécessite Julia 1.11 ou une version ultérieure.

