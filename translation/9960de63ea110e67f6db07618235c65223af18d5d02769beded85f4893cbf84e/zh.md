```
Core.set_binding_type!(module::Module, name::Symbol, [type::Type])
```

将模块 `module` 中绑定 `name` 的声明类型设置为 `type`。如果该绑定已经具有与 `type` 不相等的类型，则会报错。如果 `type` 参数缺失，则在未设置的情况下将绑定类型设置为 `Any`，但不会报错。

!!! compat "Julia 1.9"
    此函数需要 Julia 1.9 或更高版本。

