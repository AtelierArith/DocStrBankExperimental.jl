```
code_lowered(f, types; generated=true, debuginfo=:default)
```

返回与给定的泛型函数和类型签名匹配的方法的降级形式（IR）的数组。

如果 `generated` 为 `false`，返回的 `CodeInfo` 实例将对应于后备实现。如果不存在后备实现，将抛出错误。如果 `generated` 为 `true`，这些 `CodeInfo` 实例将对应于通过扩展生成器所产生的方法体。

关键字 `debuginfo` 控制输出中存在的代码元数据的数量。

请注意，如果 `types` 不是叶类型，并且在 `generated` 为 `true` 的情况下，任何相应的方法是 `@generated` 方法，将抛出错误。
