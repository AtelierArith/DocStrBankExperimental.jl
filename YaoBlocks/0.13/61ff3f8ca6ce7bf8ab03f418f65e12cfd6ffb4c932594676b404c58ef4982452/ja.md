```julia
projector(
    v::YaoArrayRegister.AbstractArrayReg
) -> YaoBlocks.Projector

```

量子状態ベクトル `v` を持つ [`Projector`](@ref) を作成します。

### 例

```jldoctest; setup=:(using YaoBlocks, YaoArrayRegister)
julia> projector(rand_state(3))
|s⟩⟨s|, nqudits = 3
```
