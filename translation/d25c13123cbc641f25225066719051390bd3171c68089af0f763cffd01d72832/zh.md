```
@goto name
```

`@goto name` 无条件跳转到位置 [`@label name`](@ref) 的语句。

`@label` 和 `@goto` 不能创建跳转到不同的顶级语句。尝试会导致错误。要仍然使用 `@goto`，请将 `@label` 和 `@goto` 包含在一个块中。
