```julia
reflect(
    v::YaoArrayRegister.AbstractArrayReg
) -> YaoBlocks.ReflectGate{D, T, Irrational{:π}, AT} where {D, T, AT<:(YaoArrayRegister.AbstractArrayReg{D, T})}
reflect(
    v::YaoArrayRegister.AbstractArrayReg,
    θ::Real
) -> YaoBlocks.ReflectGate{_A, T, Tt, AT} where {_A, Tt<:Real, T, AT<:(YaoArrayRegister.AbstractArrayReg{_A, T})}

```

量子状態ベクトル `v` に関して [`ReflectGate`](@ref) を作成します。

### 例

```jldoctest; setup=:(using YaoBlocks, YaoArrayRegister)
julia> reflect(rand_state(3))
Time Evolution Δt = π, tol = 1.0e-7
|s⟩⟨s|, nqudits = 3
```
