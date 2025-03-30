```
isnumeric(c::AbstractChar) -> Bool
```

测试一个字符是否为数字。如果一个字符属于 Unicode 一般类别 Number，则该字符被归类为数字，即其类别代码以 'N' 开头的字符。

请注意，这个广泛的类别包括字符如 ¾ 和 ௰。使用 [`isdigit`](@ref) 来检查一个字符是否是 0 到 9 之间的十进制数字。

# 示例

```jldoctest
julia> isnumeric('௰')
true

julia> isnumeric('9')
true

julia> isnumeric('α')
false

julia> isnumeric('❤')
false
```
