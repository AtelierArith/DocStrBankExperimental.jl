```
isdone(itr, [state]) -> Union{Bool, Missing}
```

此函数为迭代器完成提供了快速路径提示。这对于希望避免消耗元素（如果它们不会暴露给用户）状态迭代器非常有用（例如，在检查 `isempty` 或 `zip` 中的完成状态时）。

希望选择此功能的状态迭代器应定义一个 `isdone` 方法，该方法根据迭代器是否完成返回 true/false。无状态迭代器不需要实现此函数。

如果结果为 `missing`，调用者可以继续计算 `iterate(x, state) === nothing` 以得出明确的答案。

另见 [`iterate`](@ref), [`isempty`](@ref)
