```
viewbatch(register, i::Int) -> AbstractRegister
```

Returns the `i`-th single register of a batched register. The returned instance is a view of the original register, i.e. inplace operation changes the original register directly.

### Examples

```jldoctest; setup=:(using Yao)
julia> reg = zero_state(5; nbatch=2);

julia> apply!(viewbatch(reg, 2), put(5, 2=>X));

julia> measure(reg; nshots=3)
3×2 Matrix{DitStr{2, 5, Int64}}:
 00000 ₍₂₎  00010 ₍₂₎
 00000 ₍₂₎  00010 ₍₂₎
 00000 ₍₂₎  00010 ₍₂₎
```
