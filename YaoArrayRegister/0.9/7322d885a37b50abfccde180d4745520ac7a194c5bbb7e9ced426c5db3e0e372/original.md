```
BatchedArrayReg{D,T,MT<:AbstractMatrix{T}} <: AbstractArrayReg{D}
BatchedArrayReg(raw, nbatch; nlevel=2)
BatchedArrayReg{D}(raw, nbatch)
```

Simulated batched full amplitude register type, it uses an array to represent corresponding one or a batch of quantum states. `T` is the numerical type for each amplitude, it is `ComplexF64` by default.

!!! warning
    `BatchedArrayReg` constructor will not normalize the quantum state. If you need a normalized quantum state remember to use `normalize!(register)` on the register.

