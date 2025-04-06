```
@nloops N itersym rangeexpr bodyexpr
@nloops N itersym rangeexpr preexpr bodyexpr
@nloops N itersym rangeexpr preexpr postexpr bodyexpr
```

生成 `N` 个嵌套循环，使用 `itersym` 作为迭代变量的前缀。`rangeexpr` 可以是一个匿名函数表达式，或者是一个简单的符号 `var`，在这种情况下，范围为 `axes(var, d)`，其中 `d` 是维度。

可选地，您可以提供 "pre" 和 "post" 表达式。这些表达式分别在每个循环的主体中首先和最后执行。例如：

```
@nloops 2 i A d -> j_d = min(i_d, 5) begin
    s += @nref 2 A j
end
```

将生成：

```
for i_2 = axes(A, 2)
    j_2 = min(i_2, 5)
    for i_1 = axes(A, 1)
        j_1 = min(i_1, 5)
        s += A[j_1, j_2]
    end
end
```

如果您只想要一个后表达式，请为前表达式提供 [`nothing`](@ref)。使用括号和分号，您可以提供多语句表达式。
