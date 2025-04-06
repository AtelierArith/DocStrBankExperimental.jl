```
x && y
```

短路布尔与。

另见 [`&`](@ref)、三元运算符 `? :`，以及手册中关于 [控制流](@ref man-conditional-evaluation) 的部分。

# 示例

```jldoctest
julia> x = 3;

julia> x > 1 && x < 10 && x isa Int
true

julia> x < 0 && error("expected positive x")
false
```
