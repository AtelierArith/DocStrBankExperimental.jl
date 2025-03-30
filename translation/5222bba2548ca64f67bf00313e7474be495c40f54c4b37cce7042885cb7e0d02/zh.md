`HTML(s)`: 创建一个对象，将 `s` 渲染为 html。

```
HTML("<div>foo</div>")
```

您还可以使用流来处理大量数据：

```
HTML() do io
  println(io, "<div>foo</div>")
end
```

!!! warning
    `HTML` 目前被导出以保持向后兼容性，但此导出已被弃用。建议将此类型用作 [`Docs.HTML`](@ref) 或从 `Docs` 显式导入。

