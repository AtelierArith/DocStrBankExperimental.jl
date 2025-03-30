"     get*test*counts(::AbstractTestSet) -> TestCounts

递归函数，直接在测试集中计算每种类型的测试结果数量，并在子测试集中进行汇总。

自定义的 `AbstractTestSet` 应该实现此函数，以便其总数能够与 `DefaultTestSet` 一起被计算和显示。

如果自定义的 `TestSet` 没有实现此功能，则打印将回退为报告失败的 `x` 和持续时间的 `?s`。"
