```
detect_unbound_args(mod1, mod2...; recursive=false, allowed_undefineds=nothing)
```

返回一个可能具有未绑定类型参数的 `Method` 向量。使用 `recursive=true` 在所有子模块中进行测试。

默认情况下，任何未定义的符号都会触发警告。可以通过提供一个 `GlobalRef` 的集合来抑制此警告，以跳过警告。例如，设置

```
allowed_undefineds = Set([GlobalRef(Base, :active_repl),
                          GlobalRef(Base, :active_repl_backend)])
```

将抑制关于 `Base.active_repl` 和 `Base.active_repl_backend` 的警告。

!!! compat "Julia 1.8"
    `allowed_undefineds` 至少需要 Julia 1.8。

