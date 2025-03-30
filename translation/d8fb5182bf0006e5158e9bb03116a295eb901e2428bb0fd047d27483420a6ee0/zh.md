```
isuppercase(c::AbstractChar) -> Bool
```

测试一个字符是否是大写字母（根据Unicode标准的`Uppercase`派生属性）。

另见 [`islowercase`](@ref)。

# 示例

```jldoctest
julia> isuppercase('γ')
false

julia> isuppercase('Γ')
true

julia> isuppercase('❤')
false
```
