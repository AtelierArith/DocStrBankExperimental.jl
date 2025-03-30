```
propertynames(x, private=false)
```

获取对象 `x` 的属性（`x.property`）的元组或向量。这通常与 [`fieldnames(typeof(x))`](@ref) 相同，但重载 [`getproperty`](@ref) 的类型通常也应该重载 `propertynames` 以获取该类型实例的属性。

`propertynames(x)` 可能只返回作为 `x` 文档接口一部分的“公共”属性名称。如果您希望它还返回用于内部使用的“私有”属性名称，请将可选的第二个参数设置为 `true`。在 `x.` 上的 REPL 标签补全仅显示 `private=false` 属性。

另请参见：[`hasproperty`](@ref)，[`hasfield`](@ref)。
