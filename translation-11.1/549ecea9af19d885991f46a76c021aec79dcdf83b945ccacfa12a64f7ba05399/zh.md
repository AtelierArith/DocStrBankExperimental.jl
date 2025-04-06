```
Test.Error <: Test.Result
```

测试条件由于异常无法评估，或者评估为除 [`Bool`](@ref) 之外的其他内容。在 `@test_broken` 的情况下，它用于指示发生了意外的 `Pass` `Result`。
