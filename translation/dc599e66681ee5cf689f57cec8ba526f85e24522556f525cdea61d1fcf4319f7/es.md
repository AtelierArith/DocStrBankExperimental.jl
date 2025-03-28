```
GenericMemory{kind::Symbol, T, addrspace=Core.CPU} <: DenseVector{T}
```

Tamaño fijo [`DenseVector{T}`](@ref DenseVector).

`kind` puede ser actualmente `:not_atomic` o `:atomic`. Para detalles sobre lo que implica `:atomic`, consulta [`AtomicMemory`](@ref)

`addrspace` actualmente solo se puede establecer en Core.CPU. Está diseñado para permitir la extensión por otros sistemas como GPUs, que podrían definir valores como:

```
module CUDA
const Generic = bitcast(Core.AddrSpace{CUDA}, 0)
const Global = bitcast(Core.AddrSpace{CUDA}, 1)
end
```

La semántica exacta de estos otros addrspaces está definida por el backend específico, pero generará un error si el usuario intenta acceder a estos en la CPU.

!!! compat "Julia 1.11"
    Este tipo requiere Julia 1.11 o posterior.

