```
keytype(type)
```

辞書型のキータイプを取得します。[`eltype`](@ref)と似たように動作します。

# 例

```jldoctest
julia> keytype(Dict(Int32(1) => "foo"))
Int32
```
