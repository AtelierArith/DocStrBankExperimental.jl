```
函数
```

函数是用 `function` 关键字定义的：

```julia
function add(a, b)
    return a + b
end
```

或者使用简写形式：

```julia
add(a, b) = a + b
```

使用 [`return`](@ref) 关键字的方式与其他语言完全相同，但通常是可选的。没有显式 `return` 语句的函数将返回函数体中的最后一个表达式。
