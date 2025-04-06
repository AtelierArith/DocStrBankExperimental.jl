```
detect_ambiguities(mod1, mod2...; recursive=false,
                                  ambiguous_bottom=false,
                                  allowed_undefineds=nothing)
```

返回一个包含在指定模块中定义的模糊方法的 `(Method,Method)` 对的向量。使用 `recursive=true` 在所有子模块中进行测试。

`ambiguous_bottom` 控制是否包含仅由 `Union{}` 类型参数触发的模糊性；在大多数情况下，您可能希望将其设置为 `false`。请参见 [`Base.isambiguous`](@ref)。

有关 `allowed_undefineds` 的解释，请参见 [`Test.detect_unbound_args`](@ref)。

!!! compat "Julia 1.8"
    `allowed_undefineds` 至少需要 Julia 1.8。

