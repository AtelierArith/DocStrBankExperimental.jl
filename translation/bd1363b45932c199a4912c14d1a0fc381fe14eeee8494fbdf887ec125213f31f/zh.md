```
isletter(c::AbstractChar) -> Bool
```

测试一个字符是否是字母。如果一个字符属于 Unicode 一般类别字母，则将其归类为字母，即类别代码以 'L' 开头的字符。

另请参见: [`isdigit`](@ref)。

# 示例

```jldoctest
julia> isletter('❤')
false

julia> isletter('α')
true

julia> isletter('9')
false
```
