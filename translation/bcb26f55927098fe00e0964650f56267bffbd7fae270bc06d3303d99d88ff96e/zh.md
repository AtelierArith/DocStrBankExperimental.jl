```
undocumented_names(mod::Module; private=false)
```

返回一个已排序的向量，包含 `module` 中未记录的符号（即缺少文档字符串）。`private=false`（默认值）仅返回使用 `public` 和/或 `export` 声明的标识符，而 `private=true` 返回模块中的所有符号（不包括以 `#` 开头的编译器生成的隐藏符号）。

另请参见: [`names`](@ref), [`Docs.hasdoc`](@ref), [`Base.ispublic`](@ref).
