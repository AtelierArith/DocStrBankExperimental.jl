```
finish(ts::AbstractTestSet)
```

对给定的测试集进行任何必要的最终处理。这是在测试块执行后由 `@testset` 基础设施调用的。

自定义的 `AbstractTestSet` 子类型应该在其父类（如果有的话）上调用 `record`，以将自己添加到测试结果树中。这可以实现为：

```julia
if get_testset_depth() != 0
    # 将此测试集附加到父测试集
    parent_ts = get_testset()
    record(parent_ts, self)
    return self
end
```
