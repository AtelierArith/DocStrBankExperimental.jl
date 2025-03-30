```
GenericMemory{kind::Symbol, T, addrspace=Core.CPU} <: DenseVector{T}
```

固定大小的 [`DenseVector{T}`](@ref DenseVector)。

`kind` 目前可以是 `:not_atomic` 或 `:atomic`。有关 `:atomic` 的详细信息，请参见 [`AtomicMemory`](@ref)

`addrspace` 目前只能设置为 Core.CPU。它旨在允许其他系统（例如 GPU）的扩展，这些系统可能定义如下值：

```
module CUDA
const Generic = bitcast(Core.AddrSpace{CUDA}, 0)
const Global = bitcast(Core.AddrSpace{CUDA}, 1)
end
```

这些其他地址空间的确切语义由特定的后端定义，但如果用户试图在 CPU 上访问这些地址空间，将会出错。

!!! compat "Julia 1.11"
    此类型需要 Julia 1.11 或更高版本。

