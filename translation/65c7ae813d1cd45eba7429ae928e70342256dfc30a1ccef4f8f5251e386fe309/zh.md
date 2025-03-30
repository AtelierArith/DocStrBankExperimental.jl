```
@ncallkw N f kw sym...
```

生成一个带有关键字参数 `kw...` 的函数调用表达式。与 [`@ncall`](@ref) 的情况一样，`sym` 代表任意数量的函数参数，最后一个参数可以是匿名函数表达式，并扩展为 `N` 个参数。

# 示例

```jldoctest
julia> using Base.Cartesian

julia> f(x...; a, b = 1, c = 2, d = 3) = +(x..., a, b, c, d);

julia> x_1, x_2 = (-1, -2); b = 0; kw = (c = 0, d = 0);

julia> @ncallkw 2 f (; a = 0, b, kw...) x
-3

```
