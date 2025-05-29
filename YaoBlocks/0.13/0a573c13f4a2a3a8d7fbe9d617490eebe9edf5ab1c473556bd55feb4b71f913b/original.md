```julia
struct Projector{D, T, AT<:(YaoArrayRegister.AbstractArrayReg{D, T})} <: YaoAPI.PrimitiveBlock{D}
```

Projection operator to target state `psi`.

### Definition

`projector(s)` defines the following operator.

$$
|s⟩ → |s⟩⟨s|
$$
