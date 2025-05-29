```julia
safe_remove!(
    reg::YaoArrayRegister.AbstractArrayReg,
    locs
) -> YaoArrayRegister.AbstractArrayReg

```

他の量子ビットと絡み合っていない量子ビットを安全に削除します。すなわち、`isseparable(reg, locs)`はtrueを返さなければなりません。

### 例

```jldoctest; setup=:(using YaoArrayRegister)
julia> reg = join(ghz_state(3), ghz_state(2));

julia> safe_remove!(copy(reg), 1:2)
ArrayReg{2, ComplexF64, Array...}
    active qubits: 3/3
    nlevel: 2

julia> safe_remove!(copy(reg), 1:3)
ERROR: Qubits at locations 1:3 are entangled with the rest qubits.
[...]
```
