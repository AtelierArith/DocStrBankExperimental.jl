```
if/elseif/else
```

`if`/`elseif`/`else` 执行条件评估，这允许根据布尔表达式的值来评估或不评估代码的某些部分。以下是 `if`/`elseif`/`else` 条件语法的结构：

```julia
if x < y
    println("x 小于 y")
elseif x > y
    println("x 大于 y")
else
    println("x 等于 y")
end
```

如果条件表达式 `x < y` 为真，则相应的代码块被评估；否则，条件表达式 `x > y` 被评估，如果它为真，则相应的代码块被评估；如果两个表达式都不为真，则评估 `else` 块。`elseif` 和 `else` 块是可选的，可以使用任意数量的 `elseif` 块。

与某些其他语言相比，条件必须是 `Bool` 类型。条件不能仅仅转换为 `Bool`。

```jldoctest
julia> if 1 end
ERROR: TypeError: non-boolean (Int64) used in boolean context
```
