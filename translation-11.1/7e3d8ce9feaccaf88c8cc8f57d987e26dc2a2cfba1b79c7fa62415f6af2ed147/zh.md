```
Sys.isbsd([os])
```

用于测试操作系统是否是BSD的衍生版本的谓词。请参阅[处理操作系统变体](@ref)中的文档。

!!! note
    Darwin内核源自BSD，这意味着在macOS系统上`Sys.isbsd()`为`true`。要从谓词中排除macOS，请使用`Sys.isbsd() && !Sys.isapple()`。

