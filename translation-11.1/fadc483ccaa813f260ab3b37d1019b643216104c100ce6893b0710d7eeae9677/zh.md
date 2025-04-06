```
task_local_storage(body, key, value)
```

调用函数 `body`，使用修改后的任务局部存储，其中 `value` 被分配给 `key`；`key` 的先前值（或缺失）在之后恢复。这对于模拟动态作用域非常有用。
