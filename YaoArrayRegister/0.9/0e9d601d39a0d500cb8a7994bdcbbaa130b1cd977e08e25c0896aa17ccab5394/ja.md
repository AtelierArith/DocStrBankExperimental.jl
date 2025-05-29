```
product_state([T=ComplexF64], dit_str; nbatch=NoBatch(), no_transpose_storage=false)
product_state([T=ComplexF64], nbits::Int, val::Int; nbatch=NoBatch(), nlevel=2, no_transpose_storage=false)
product_state([T=ComplexF64], vector; nbatch=NoBatch(), nlevel=2, no_transpose_storage=false)
```

[`ArrayReg`](@ref) の積状態を作成します。構成は、[`@bit_str`](@ref) または [`@dit_str`](@ref) を使用して定義できるディット文字列で指定できます。または、`nbits`、`val`、`nlevel` を使用して明示的に指定することもできます。[`zero_state`](@ref)、[`rand_state`](@ref)、[`uniform_state`](@ref) も参照してください。

### 例

```jldoctest; setup=:(using Yao)
julia> reg = product_state(dit"120;3"; nbatch=2)
BatchedArrayReg{3, ComplexF64, Transpose...}
    active qudits: 3/3
    nlevel: 3
    nbatch: 2

julia> measure(reg)
1×2 Matrix{BitBasis.DitStr64{3, 3}}:
 120 ₍₃₎  120 ₍₃₎

julia> product_state(bit"100"; nbatch=2);

julia> r1 = product_state(ComplexF32, bit"001"; nbatch=2);

julia> r2 = product_state(ComplexF32, [1, 0, 0]; nbatch=2);

julia> r3 = product_state(ComplexF32, 3, 0b001; nbatch=2);

julia> r1 ≈ r2   # 右から左にビット文字列を読み、左から右にベクトルを読み取るため。
true

julia> r1 ≈ r3
true
```
