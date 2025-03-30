```
instances(T::Type)
```

返回给定类型的所有实例的集合（如果适用）。主要用于枚举类型（见 `@enum`）。

# 示例

```jldoctest
julia> @enum Color red blue green

julia> instances(Color)
(red, blue, green)
```
