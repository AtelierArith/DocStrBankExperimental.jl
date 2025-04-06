```
record(ts::AbstractTestSet, res::Result)
```

将结果记录到测试集。每当包含的 `@test` 宏完成时，此函数会被 `@testset` 基础设施调用，并给出测试结果（可能是一个 `Error`）。如果在测试块内但在 `@test` 上下文之外抛出异常，也会调用此函数并传入一个 `Error`。
