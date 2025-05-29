```
ArrayReg{D,T,MT<:AbstractMatrix{T}} <: AbstractArrayRegister{D}
ArrayReg{D}(raw)
ArrayReg(raw::AbstractVecOrMat; nlevel=2)
ArrayReg(r::ArrayReg)
```

Simulated full amplitude register type, it uses an array to represent corresponding one or a batch of quantum states. `T` is the numerical type for each amplitude, it is `ComplexF64` by default.

!!! warning
    `ArrayReg` constructor will not normalize the quantum state. If you need a normalized quantum state remember to use `normalize!(register)` on the register.

