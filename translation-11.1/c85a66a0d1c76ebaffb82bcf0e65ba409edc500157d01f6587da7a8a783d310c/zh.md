```
showable(mime, x)
```

返回一个布尔值，指示对象 `x` 是否可以作为给定的 `mime` 类型进行写入。

（默认情况下，这通过检查 `typeof(x)` 的相应 [`show`](@ref) 方法的存在来自动确定。一些类型提供自定义的 `showable` 方法；例如，如果可用的 MIME 格式依赖于 `x` 的 *值*。）

# 示例

```jldoctest
julia> showable(MIME("text/plain"), rand(5))
true

julia> showable("image/png", rand(5))
false
```
