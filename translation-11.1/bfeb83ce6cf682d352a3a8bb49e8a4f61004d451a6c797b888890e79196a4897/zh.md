```
@__FILE__ -> String
```

扩展为包含宏调用的文件路径的字符串，如果通过 `julia -e <expr>` 评估，则返回空字符串。如果宏缺少解析器源信息，则返回 `nothing`。另请参见 [`PROGRAM_FILE`](@ref)。
