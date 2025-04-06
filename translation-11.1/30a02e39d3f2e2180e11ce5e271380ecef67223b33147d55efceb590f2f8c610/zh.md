```
a ? b : c
```

条件的简写形式；读作“如果 `a`，则计算 `b`，否则计算 `c`”。也称为[三元运算符](https://en.wikipedia.org/wiki/%3F:)。

这种语法等价于 `if a; b else c end`，但通常用于强调作为更大表达式一部分的值 `b` 或 `c`，而不是计算 `b` 或 `c` 可能产生的副作用。

有关更多详细信息，请参见手册中的[控制流](@ref man-conditional-evaluation)部分。

# 示例

```jldoctest
julia> x = 1; y = 2;

julia> x > y ? println("x is larger") : println("x is not larger")
x is not larger

julia> x > y ? "x is larger" : x == y ? "x and y are equal" : "y is larger"
"y is larger"
```
