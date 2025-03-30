```
displaysize([io::IO]) -> (lines, columns)
```

返回可以用于渲染输出到此 `IO` 对象的屏幕的名义大小。如果未提供输入，则读取环境变量 `LINES` 和 `COLUMNS`。如果这些未设置，则返回默认大小 `(24, 80)`。

# 示例

```jldoctest
julia> withenv("LINES" => 30, "COLUMNS" => 100) do
           displaysize()
       end
(30, 100)
```

要获取您的 TTY 大小，

```julia-repl
julia> displaysize(stdout)
(34, 147)
```
