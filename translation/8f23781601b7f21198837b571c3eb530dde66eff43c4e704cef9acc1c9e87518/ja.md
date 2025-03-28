```
fieldnames(x::DataType)
```

`DataType`のフィールド名を持つタプルを取得します。

関連情報としては、[`propertynames`](@ref)、[`hasfield`](@ref)があります。

# 例

```jldoctest
julia> fieldnames(Rational)
(:num, :den)

julia> fieldnames(typeof(1+im))
(:re, :im)
```
