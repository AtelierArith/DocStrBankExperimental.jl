```
TestCounts
```

用于递归收集测试集结果以供显示的状态。

字段：

  * `customized`: 函数 `get_test_counts` 是否为此计数对象所对应的 `AbstractTestSet` 定制。如果定义了自定义方法，请始终将 `true` 传递给构造函数。
  * `passes`: 通过的 `@test` 调用次数。
  * `fails`: 失败的 `@test` 调用次数。
  * `errors`: 出错的 `@test` 调用次数。
  * `broken`: 破损的 `@test` 调用次数。
  * `passes`: 通过的 `@test` 调用的累计次数。
  * `fails`: 失败的 `@test` 调用的累计次数。
  * `errors`: 出错的 `@test` 调用的累计次数。
  * `broken`: 破损的 `@test` 调用的累计次数。
  * `duration`: 相关 `AbstractTestSet` 运行的总时长，以格式化的 `String` 表示。
