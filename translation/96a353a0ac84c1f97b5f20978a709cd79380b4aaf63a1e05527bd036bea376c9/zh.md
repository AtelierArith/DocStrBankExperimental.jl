```
uuid5(ns::UUID, name::String) -> UUID
```

生成一个版本 5（基于命名空间和域）的全局唯一标识符（UUID），如 RFC 4122 所规定。

!!! compat "Julia 1.1"
    此函数至少需要 Julia 1.1。


# 示例

```jldoctest
julia> using Random

julia> rng = Xoshiro(123);

julia> u4 = uuid4(rng)
UUID("856e446e-0c6a-472a-9638-f7b8557cd282")

julia> u5 = uuid5(u4, "julia")
UUID("2df91e3f-da06-5362-a6fe-03772f2e14c9")
```
