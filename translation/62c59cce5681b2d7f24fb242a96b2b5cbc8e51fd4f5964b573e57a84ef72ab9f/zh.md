```
ispunct(c::AbstractChar) -> Bool
```

测试一个字符是否属于 Unicode 一般类别标点符号，即类别代码以 'P' 开头的字符。

# 示例

```jldoctest
julia> ispunct('α')
false

julia> ispunct('/')
true

julia> ispunct(';')
true
```
