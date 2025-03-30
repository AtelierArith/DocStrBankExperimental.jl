```
estate::EscapeState
```

扩展的格映射参数和 SSA 值到表示为 [`EscapeInfo`](@ref) 的逃逸信息。对 SSA IR 元素 `x` 施加的逃逸信息可以通过 `estate[x]` 检索。
