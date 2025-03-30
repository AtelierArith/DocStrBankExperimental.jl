```
isascii(c::Union{AbstractChar,AbstractString}) -> Bool
```

测试一个字符是否属于 ASCII 字符集，或者一个字符串的所有元素是否都属于 ASCII 字符集。

# 示例

```jldoctest
julia> isascii('a')
true

julia> isascii('α')
false

julia> isascii("abc")
true

julia> isascii("αβγ")
false
```

例如，`isascii` 可以作为 [`filter`](@ref) 或 [`replace`](@ref) 的谓词函数，分别用于移除或替换非 ASCII 字符：

```jldoctest
julia> filter(isascii, "abcdeγfgh") # 丢弃非 ASCII 字符
"abcdefgh"

julia> replace("abcdeγfgh", !isascii=>' ') # 用空格替换非 ASCII 字符
"abcde fgh"
```
