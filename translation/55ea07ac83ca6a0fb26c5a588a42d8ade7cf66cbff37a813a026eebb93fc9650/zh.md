```
print_test_results(ts::AbstractTestSet, depth_pad=0)
```

打印 `AbstractTestSet` 的结果作为格式化表格。

`depth_pad` 指的是在所有输出前应添加多少填充。

在 `Test.finish` 内部调用，如果 `finish` 的测试集是最上层的测试集。
