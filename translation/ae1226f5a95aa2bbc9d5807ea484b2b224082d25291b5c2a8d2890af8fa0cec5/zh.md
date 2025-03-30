`Text(s)`: 创建一个对象，将 `s` 渲染为纯文本。

```
Text("foo")
```

您还可以使用流来处理大量数据：

```
Text() do io
  println(io, "foo")
end
```

!!! warning
    `Text` 目前被导出以保持向后兼容性，但此导出已被弃用。建议将此类型用作 [`Docs.Text`](@ref) 或从 `Docs` 显式导入。

