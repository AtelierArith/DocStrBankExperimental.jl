```
normalize!(r::AbstractArrayReg)
```

レジスタ `r` をその 2-ノルムで正規化します。レジスタは直接変更されます。

### 例

以下のコードは正規化された GHZ 状態を作成します。

```julia
julia> reg = product_state(bit"000") + product_state(bit"111");

julia> norm(reg)
1.4142135623730951

julia> isnormalized(reg)
false

julia> normalize!(reg);

julia> isnormalized(reg)
true
```
