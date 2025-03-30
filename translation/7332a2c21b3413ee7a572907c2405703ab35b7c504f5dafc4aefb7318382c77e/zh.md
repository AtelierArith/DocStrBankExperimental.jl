```
methodswith(typ[, module or function]; supertypes::Bool=false])
```

返回一个包含类型为 `typ` 的参数的方法数组。

可选的第二个参数将搜索限制在特定的模块或函数（默认是所有顶级模块）。

如果关键字 `supertypes` 为 `true`，还会返回具有父类型 `typ` 的参数，排除类型 `Any`。

另见: [`methods`](@ref).
