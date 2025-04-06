```
islowercase(c::AbstractChar) -> Bool
```

测试一个字符是否是小写字母（根据 Unicode 标准的 `Lowercase` 派生属性）。

另见 [`isuppercase`](@ref)。

# 示例

```jldoctest
julia> islowercase('α')
true

julia> islowercase('Γ')
false

julia> islowercase('❤')
false
```
