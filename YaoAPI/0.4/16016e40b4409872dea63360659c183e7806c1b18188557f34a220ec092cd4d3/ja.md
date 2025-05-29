```
viewbatch(register, i::Int) -> AbstractRegister
```

バッチ登録の `i` 番目の単一レジスタを返します。返されるインスタンスは元のレジスタのビューであり、すなわちインプレース操作は元のレジスタを直接変更します。

### 例

```jldoctest; setup=:(using Yao)
julia> reg = zero_state(5; nbatch=2);

julia> apply!(viewbatch(reg, 2), put(5, 2=>X));

julia> measure(reg; nshots=3)
3×2 Matrix{DitStr{2, 5, Int64}}:
 00000 ₍₂₎  00010 ₍₂₎
 00000 ₍₂₎  00010 ₍₂₎
 00000 ₍₂₎  00010 ₍₂₎
```
