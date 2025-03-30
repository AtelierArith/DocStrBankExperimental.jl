```
isequal_normalized(s1::AbstractString, s2::AbstractString; casefold=false, stripmark=false, chartransform=identity)
```

返回 `s1` 和 `s2` 是否是规范等价的 Unicode 字符串。如果 `casefold=true`，则忽略大小写（执行 Unicode 大小写折叠）；如果 `stripmark=true`，则去除变音符号和其他组合字符。

与 [`Unicode.normalize`](@ref) 一样，您还可以通过 `chartransform` 关键字传递任意函数（将 `Integer` 代码点映射到代码点）以执行自定义规范化，例如 [`Unicode.julia_chartransform`](@ref)。

!!! compat "Julia 1.8"
    `isequal_normalized` 函数是在 Julia 1.8 中添加的。


# 示例

例如，字符串 `"noël"` 可以通过两种规范等价的方式在 Unicode 中构造，具体取决于 `"ë"` 是由单个代码点 U+00EB 形成，还是由 ASCII 字符 `'e'` 后跟 U+0308 组合变音符号字符形成。

```jldoctest
julia> s1 = "noël"
"noël"

julia> s2 = "noël"
"noël"

julia> s1 == s2
false

julia> isequal_normalized(s1, s2)
true

julia> isequal_normalized(s1, "noel", stripmark=true)
true

julia> isequal_normalized(s1, "NOËL", casefold=true)
true
```
