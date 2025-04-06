```
unwatch_folder(path::AbstractString)
```

停止对 `path` 的后台更改跟踪。建议在另一个任务等待 `watch_folder` 在同一路径上返回时不要执行此操作，因为结果可能是不可预测的。
