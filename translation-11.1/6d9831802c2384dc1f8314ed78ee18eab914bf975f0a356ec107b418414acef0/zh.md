```
var
```

语法 `var"#example#"` 指的是一个名为 `Symbol("#example#")` 的变量，即使 `#example#` 不是一个有效的 Julia 标识符名称。

这对于与具有不同有效标识符构造规则的编程语言的互操作性非常有用。例如，要在你的 Julia 代码中引用 `R` 变量 `draw.segments`，你可以使用 `var"draw.segments"`。

它也用于 `show` 经过宏卫生处理或包含无法正常解析的变量名称的 Julia 源代码。

请注意，这种语法需要解析器支持，因此它是由解析器直接扩展的，而不是作为普通字符串宏 `@var_str` 实现的。

!!! compat "Julia 1.3"
    这种语法至少需要 Julia 1.3。

